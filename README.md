# Masterix Composer Registry

Public Composer metadata catalog for approved Masterix private packages.

The catalog is published at
`https://masterix-sistemas.github.io/composer-registry`.

`satis.json` is the reviewed allowlist of package repositories. It intentionally
does not configure Satis archives, so the Pages deployment contains Composer
metadata only. Package source and any GitHub-provided distribution archives
remain authenticated and are served directly by GitHub.

The **publish** workflow is run manually through **Run workflow**. Each run
rebuilds and deploys the complete catalog from the reviewed `satis.json`
allowlist; it has no inputs and receives no dispatches from package
repositories. Satis fetches every configured VCS source and publishes its
stable versions that satisfy each package constraint. The `require` object is
the explicit package allowlist: use `"*"` for each approved package so releases
are not constrained to a manually maintained minimum version.

For each build, the workflow derives the Masterix GitHub repositories from
`satis.json` and mints a short-lived read-only GitHub App token scoped to all
of them. Adding another approved package therefore requires only its reviewed
repository and constraint in `satis.json`. Credential values are stored only
as GitHub Actions secrets; neither the repository nor the generated catalog
contains credentials.
