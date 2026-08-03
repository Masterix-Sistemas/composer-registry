# Consumer and local integration

The Registry serves Composer metadata for approved packages. A consumer still
needs its own authorized source access to download private package contents.

## Released package consumption

Use the released package through the consumer's tracked Composer configuration.
The [Platform release and consumer handoff guide](https://github.com/Masterix-Sistemas/platform/blob/main/docs/release-and-consumption.md)
owns the detailed host-side procedure and the stable dependency selection.

The Registry does not require or publish a consumer credential, and it does not
proxy source archives.

## Local plugin integration

Testing an unreleased plugin checkout is a consumer-side concern. Follow
Platform's [local Identity & Access integration guide](https://github.com/Masterix-Sistemas/platform/blob/main/docs/integrating-identity-access.md)
for ignored local overrides, checkout integration, and container setup.

Keep these values replaceable in any cross-repository instructions:

| Variable | Identity & Access example | Owner |
| --- | --- | --- |
| Package name | `masterix/identity-access` | The plugin and its reviewed Registry entry |
| Stable constraint | `^0.1` | The consumer's tracked Composer configuration |
| Local checkout path | A developer's local plugin checkout | The consumer's ignored local override |
| Container mount path | `/opt/identity-access` | The consumer's ignored container override |

The local path repository, `@dev` selection, checkout path, and mount override
do not belong in `satis.json`, generated catalog files, or tracked consumer
manifests. Never commit a developer's absolute path or local credential.
