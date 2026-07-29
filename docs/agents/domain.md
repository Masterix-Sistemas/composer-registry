# Domain Docs

Composer Registry is one bounded context. There is no committed `CONTEXT.md` or ADR directory yet. Use `README.md` and the reviewed `satis.json` allowlist as current discovery material: the registry publishes public Composer metadata for approved private package sources and does not publish source archives.

`/domain-modeling` creates `CONTEXT.md` and `docs/adr/` lazily when it resolves a genuine glossary term, invariant, lifecycle rule, ownership boundary, or durable architecture decision. Do not create a context map or split context-scoped documentation merely because the workflow has build and deployment jobs.

Once created, `CONTEXT.md` is the glossary and `docs/adr/NNNN-*.md` holds repository-wide ADRs. Surface any contradiction between a proposed change and an ADR or the catalog's security boundary rather than silently changing the interpretation.
