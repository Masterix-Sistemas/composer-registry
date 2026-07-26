# Masterix Composer Registry

Public Composer metadata catalog for approved Masterix private packages.

The catalog is published at
`https://masterix-sistemas.github.io/composer-registry`.

`satis.json` is the reviewed allowlist of package repositories. It intentionally
does not configure Satis archives, so the Pages deployment contains Composer
metadata only. Package source and any GitHub-provided distribution archives
remain authenticated and are served directly by GitHub.

Run the **publish** workflow manually to rebuild and deploy the catalog. The
workflow mints a short-lived token from the `composer-registry-reader` GitHub
App using `COMPOSER_REGISTRY_READER_APP_ID` and
`COMPOSER_REGISTRY_READER_PRIVATE_KEY`; that App needs read-only Contents
access only to the repositories named in `satis.json`.
