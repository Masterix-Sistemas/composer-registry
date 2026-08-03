# Release handoff

A plugin release and a Composer Registry publication are separate events. A
plugin release never dispatches, rebuilds, or deploys the Registry
automatically.

## Handoff sequence

For each future private plugin:

1. Complete the plugin's package-native release readiness and tests. The
   [Identity & Access release guide](https://github.com/Masterix-Sistemas/identity-access/blob/main/docs/release.md)
   is the concrete example of that owner boundary.
2. Establish the Registry's read-only source access before admitting the
   plugin. Operational access details remain outside this repository.
3. Submit a reviewed Registry change that adds the plugin source and package
   name to [`satis.json`](../satis.json).
4. Merge the reviewed Registry change.
5. Create the plugin's stable release.
6. Manually run the [publication workflow](publication.md).

The order matters: a package is not discoverable merely because its source
repository released a version, and a Registry allowlist change is not a
publication event by itself.

## Ownership handoff

- The plugin repository owns its package name, stable release constraint, and
  release lifecycle.
- The Registry owns admission and catalog publication.
- Platform owns the consumer's Composer configuration and any local checkout
  override. Its [release and consumer handoff guide](https://github.com/Masterix-Sistemas/platform/blob/main/docs/release-and-consumption.md)
  describes the consumer side.

Do not add plugin-specific release commands, credentials, private keys, or
installation instructions to the Registry guide.
