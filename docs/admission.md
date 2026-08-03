# Plugin admission

Admission is a reviewed Registry change. It is not a side effect of releasing
a plugin and it does not publish the catalog automatically.

## Admission checklist

Before requesting a Registry change, confirm that:

1. The plugin is ready for its own package-native release lifecycle, including
   Release Please readiness and package-native tests.
2. The Registry's read-only GitHub App reader access has been established for
   the publication workflow. Operational installation details remain outside
   this repository.
3. A reviewed change adds the plugin's Masterix GitHub HTTPS VCS URL under
   `repositories` in [`satis.json`](../satis.json).
4. The same reviewed change adds the plugin's Composer package name under
   `require`.
5. The Registry change is merged before publication is attempted.
6. The plugin has a stable release before the catalog is published.

For the current concrete example, the source URL and package name are the
`identity-access` entries already present in `satis.json`. Future guides must
replace those values with the candidate plugin's reviewed values; do not copy
the example as a universal package configuration.

## Review boundary

The allowlist is the admission boundary. Do not add packages directly to
generated `public/` files, bypass review, or treat a source release as
permission to publish.

The Registry catalog contains Composer metadata only. Source retrieval remains
authenticated by the consumer and the Registry does not proxy source archives
or publish credentials.
