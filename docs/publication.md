# Manual publication

Catalog publication is an explicit maintainer action. A plugin release never
dispatches the Registry workflow automatically.

## Run the workflow

After the reviewed admission change is merged and the admitted plugin has a
stable release:

1. Open **Actions** in this repository.
2. Select the [`publish` workflow](../.github/workflows/publish.yml).
3. Choose **Run workflow** for the intended revision. The workflow is exposed
   through `workflow_dispatch` and has no release-triggered inputs.
4. Wait for the `build`, `deploy`, and `verify-consumer` jobs to succeed.

The build derives its approved source set from `satis.json`, produces Composer
metadata, checks that each required package is represented, and rejects archive
output. The deployment publishes the generated metadata to GitHub Pages. The
consumer verification fetches the deployed catalog and installs the allowlisted
packages through Composer using the established read-only GitHub App reader
access for private source retrieval.

## Verification boundary

Successful publication means the catalog is available as metadata and the
consumer verification passes. It does not make private source archives public
and it does not transfer consumer authentication ownership to the Registry.

Do not paste credential values into workflow inputs, logs, issues, pull
requests, or documentation. The names-only Actions inventory is maintained in
the [credential inventory](credential-inventory.md).
