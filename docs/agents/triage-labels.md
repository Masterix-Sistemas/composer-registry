# Triage Roles

Linear statuses represent the mutually exclusive lifecycle; Engineer-team labels represent these orthogonal roles. Remove a superseded role label whenever its meaning no longer applies.

| Canonical role | Linear representation | Entry criteria | Allowed next state |
| --- | --- | --- | --- |
| `needs-triage` | `Backlog` + `needs-triage` | Intake has not been evaluated. | `Backlog` or `Todo` after triage; `Canceled` if declined. |
| `needs-info` | `Backlog` + `needs-info` | A specific unanswered question prevents evaluation or implementation. Comment with the question. | `Backlog` after information arrives; `Canceled` if it will not arrive. |
| `ready-for-agent` | `Todo` + `ready-for-agent` | Audited specification, ready implementation ticket graph, explicit blockers, and owned evidence responsibilities exist. | `In Progress`, `Backlog` when assumptions change, or `Canceled`. |
| `ready-for-human` | `Todo` + `ready-for-human` | Work is actionable but needs an authorized human decision or human-owned implementation. Comment with the reason. | `In Progress`, `Backlog`, or `Canceled`. |
| `wontfix` | `Canceled` + `wontfix` | The request is deliberately not actioned. Record the rationale in a comment. | Terminal; reopen only after a new decision. |

`Bug` is the category label for a defect. Use `Feature` for an enhancement that adds a capability; use `Improvement` for an enhancement to an existing capability. Categories do not replace a triage role or lifecycle status.
