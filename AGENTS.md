# Agent Instructions

## Agent Skills Configuration

### Issue tracker

Planning artifacts are tracked in Linear under the Engineer team and Masterix Hub project. See `docs/agents/issue-tracker.md`.

### Triage roles

Canonical triage roles use Engineer-team labels and lifecycle statuses. See `docs/agents/triage-labels.md`.

### Domain docs

Uses a single-context layout with lazily created domain records. See `docs/agents/domain.md`.

### Delivery

Changes ship through a squash pull request to `main`; a Linear ticket is Done only after that pull request is merged and any required catalog publication succeeds. See `docs/agents/delivery.md`.
