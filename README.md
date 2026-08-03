# Masterix Composer Registry

The Composer Registry is the public Composer metadata catalog for approved
Masterix private packages. Its catalog is published at
`https://masterix-sistemas.github.io/composer-registry`.

## Related guides

- [Identity & Access plugin guide](https://github.com/Masterix-Sistemas/identity-access)
  covers the private-plugin release policy and uses
  `masterix/identity-access` as a concrete example.
- [Platform guide](https://github.com/Masterix-Sistemas/platform)
  covers consuming released packages and integrating a local plugin checkout.

## Registry guides

The [user-facing guides](docs/README.md) keep the Registry-owned procedures
together and link to the plugin and Platform procedures that belong elsewhere:

- [Release handoff](docs/release-handoff.md) — the boundary between a stable
  plugin release and manual catalog publication.
- [Plugin admission](docs/admission.md) — the reviewed source and package
  allowlist path.
- [Manual publication](docs/publication.md) — build, deploy, and consumer
  verification from the `publish` workflow.
- [Consumer and local integration](docs/consumer-integration.md) — metadata-only
  consumption and the Platform-owned local checkout path.
- [Credential inventory](docs/credential-inventory.md) — names-only Actions
  metadata and observed workflow references.

The Registry owns catalog admission and publication. Plugin repositories own
their release policy, and Platform owns consumer and local-integration
configuration.

## Catalog boundary and reader access

`satis.json` is the reviewed allowlist of package repositories. Its
`repositories` entries identify approved VCS sources, and its `require` object
is the explicit package allowlist. Use `"*"` for an admitted package so its
stable releases are not constrained by a manually maintained minimum version.

The Satis configuration intentionally has no archive configuration. A Pages
deployment contains Composer metadata only: no source, credentials, generated
archives, or other distribution artifacts. Source retrieval remains
authenticated through GitHub; the Registry does not proxy or expose it.

For each build, the workflow derives the Masterix GitHub repositories from
`satis.json` and mints a short-lived, read-only GitHub App token scoped to
those repositories. The GitHub App's reader access must be established before
admitting a source. Secret values and installation details remain operational
configuration and are not documented or stored in this repository.

## Publish a released package

Publication is deliberately manual. A plugin release never dispatches,
rebuilds, or deploys this catalog automatically.

After a plugin has a stable release and is already admitted to the reviewed
allowlist:

1. Open **Actions** in this repository, select the **publish** workflow, and
   choose **Run workflow** for the intended revision. The workflow is exposed
   only through `workflow_dispatch` and has no inputs.
2. Wait for the `build` and `deploy` jobs to succeed. The build verifies that
   every allowed package has catalog metadata and that no archive output was
   produced.
3. Confirm the `verify-consumer` job succeeds. It fetches the deployed
   `packages.json`, configures Composer to use the deployed catalog, and
   installs every allowlisted package with authenticated GitHub source access.

This verifies the deployed catalog from a consumer seam without placing a
credential in the catalog or README. A consumer still needs its own authorized
GitHub access to retrieve private package source.

## Admit another private plugin

Admission is a reviewed Registry change, not a side effect of releasing a
plugin. Before opening that change, ensure that:

1. The plugin repository is ready for its own Release Please lifecycle and can
   create stable releases.
2. The Registry GitHub App has established read-only access to the plugin
   repository.
3. A reviewed change adds the plugin's Masterix GitHub HTTPS VCS URL in the
   form `https://github.com/Masterix-Sistemas/<repository>.git` under
   `repositories`, and its package name under `require` in `satis.json`. The
   reader-auth action derives its authorized repositories from that URL form.
4. The reviewed Registry change has merged, the plugin has a stable release,
   and a Registry maintainer manually runs **publish** as described above.

Only this reviewed source-and-allowlist path makes a package discoverable in
the catalog. Do not add a package directly to generated `public/` files, and
do not bypass the review or reader-access gate.

## Reusable plugin and local-development variables

Identity & Access is an example, not a universal configuration. For another
private plugin, replace these values in the owning plugin and Platform guides:

- **Package name:** `masterix/identity-access`; owned by the plugin and its
  reviewed Registry allowlist entry.
- **Stable constraint:** `^0.1`; owned by Platform's tracked Composer manifest.
- **Local checkout path:** a developer's local plugin checkout; owned by an
  ignored Platform override.
- **Container mount path:** `/opt/identity-access`; owned by an ignored
  Platform Compose override.

Released packages always resolve through Platform's tracked Composer
configuration. A local `path` repository and `@dev` selection belong only in
the ignored Platform overrides described by the
[Platform guide](https://github.com/Masterix-Sistemas/platform). They do not
belong in `satis.json`, generated catalog files, or tracked Platform manifests.
