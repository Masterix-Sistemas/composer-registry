# Masterix Composer Registry

Public Composer metadata catalog for approved Masterix private packages.

The catalog is published at
`https://masterix-sistemas.github.io/composer-registry`.

`satis.json` is the reviewed allowlist of package repositories. It intentionally
does not configure Satis archives, so the Pages deployment contains Composer
metadata only. Package source and any GitHub-provided distribution archives
remain authenticated and are served directly by GitHub.

The **publish** workflow rebuilds and deploys the catalog in either case:

- automatically after Identity & Access Release Please creates a release; or
- manually through **Run workflow**, for recovery and refreshes.

The release workflow mints a short-lived, repository-scoped token from the
`composer-registry-dispatcher` GitHub App using
`COMPOSER_REGISTRY_DISPATCHER_APP_ID` and
`COMPOSER_REGISTRY_DISPATCHER_PRIVATE_KEY`. It sends a
`composer-package-released` repository dispatch only when Release Please
reports that it created a release. The catalog validates the package release
payload before building.

For each build, the workflow mints a short-lived token from the
`composer-registry-reader` GitHub App using
`COMPOSER_REGISTRY_READER_APP_ID` and
`COMPOSER_REGISTRY_READER_PRIVATE_KEY`; that App needs read-only Contents
access only to the repositories named in `satis.json`.
