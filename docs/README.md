# Composer Registry guides

The Composer Registry publishes public Composer metadata for approved private
packages. It does not publish source archives, credentials, or private package
contents.

## Choose a guide

| Need | Guide | Owning boundary |
| --- | --- | --- |
| Hand a stable plugin release to the Registry | [Release handoff](release-handoff.md) | Plugin release readiness and Registry publication are separate events. |
| Admit another private plugin | [Plugin admission](admission.md) | The Registry owns the reviewed source and package allowlist. |
| Publish the catalog manually | [Manual publication](publication.md) | The Registry owns the manually dispatched build, deployment, and verification. |
| Consume a released package or test a local checkout | [Consumer and local integration](consumer-integration.md) | Platform owns consumer configuration and local overrides. |
| Review configured Actions credential metadata | [Credential inventory](credential-inventory.md) | This page records names and references only. |

## Repository boundaries

- The Registry owns the reviewed `satis.json` allowlist and manual catalog
  publication.
- A plugin repository owns package-native development, release readiness, and
  release policy. [Identity & Access release guidance](https://github.com/Masterix-Sistemas/identity-access/blob/main/docs/release.md)
  is the concrete example.
- Platform owns stable dependency selection, consumer authentication, and
  local plugin integration. See its [release and consumer handoff guide](https://github.com/Masterix-Sistemas/platform/blob/main/docs/release-and-consumption.md)
  and [local Identity & Access integration guide](https://github.com/Masterix-Sistemas/platform/blob/main/docs/integrating-identity-access.md).

## Privacy boundary

These guides intentionally document only public workflow behavior and
metadata-only credential inventory. They do not record secret values, private
keys, tokens, installation identifiers, installation details, or developer
machine paths.
