# Issue Tracker: Linear

Planning artifacts for `Masterix-Sistemas/composer-registry` belong in Linear's **Engineer** team and **Masterix Hub** project. GitHub remains the code host for commits, pull requests, Actions, GitHub Pages, and reviews.

Before creating a specification, map, or ticket, search Linear for a matching issue. A specification is a Linear issue; implementation tickets are separate child issues when supported, otherwise related issues in the same project. Include the repository name, stable MAS identifier, acceptance obligations, and a link to the parent specification. Use Linear's native parent/related and blocking relationships; do not make prose the only dependency record.

Use the Linear MCP tools to search, read, create, update, and comment on issues. Store immutable specification revisions in their issue body or a dated comment; tickets link the exact specification identifier and revision they implement. If Linear is unavailable, do not create duplicate GitHub Issues or local tracker files: preserve the local implementation evidence and report the tracker transition as blocked until access returns.

Move implementation work to `In Progress` when it starts and to `In Review` after its GitHub pull request exists. Add the GitHub pull request URL and MAS identifier to the issue. Move it to `Done` only after the configured delivery completion event in `docs/agents/delivery.md`.

## Wayfinder operations

A map is a Linear issue labelled `wayfinder:map`, with its Notes, Decisions-so-far, and Fog in the body. Each decision child is a child or related issue labelled exactly one of `wayfinder:research`, `wayfinder:prototype`, `wayfinder:grilling`, or `wayfinder:task`.

Use native blocked-by relations for unresolved prerequisites. Claim a frontier child by assigning it to the driving developer or agent and moving it to `In Progress`. The frontier query is: children that are open, unblocked, and unassigned. Resolve a child with a Linear comment, append a linked one-line decision gist to the map when relevant, and close it only when its own completion rule is met. Create a new child for newly visible fog and record out-of-scope decisions on the map.
