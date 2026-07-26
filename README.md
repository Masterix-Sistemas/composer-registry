# Masterix Composer Registry

Public Composer metadata catalog for approved Masterix private packages.

The catalog is published at
`https://masterix-sistemas.github.io/composer-registry`.

`satis.json` is the reviewed allowlist of package repositories. It intentionally
does not configure Satis archives, so the Pages deployment contains Composer
metadata only. Package source and any GitHub-provided distribution archives
remain authenticated and are served directly by GitHub.

The **publish** workflow rebuilds and deploys the catalog in either case:

- automatically after an approved package Release Please creates a release; or
- manually through **Run workflow**, for recovery and refreshes.

The package release workflow mints a short-lived, repository-scoped GitHub App
token and sends a `composer-package-released` dispatch only when Release Please
reports that it created a release. Its payload contains only the Composer
package name and release tag. The catalog accepts the event only when that
package appears in its reviewed `satis.json` allowlist, then verifies the
dispatched tag in the generated metadata.

For each build, the workflow mints a short-lived read-only GitHub App token for
the repositories named in `satis.json`. Credential values are stored only as
GitHub Actions secrets; neither the repository nor the generated catalog
contains credentials.
