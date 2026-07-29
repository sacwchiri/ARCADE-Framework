# Workflow: Documentation Curation

Use this workflow when documentation has been created, renamed, superseded,
contradicted, or changed by meaningful production work.

## Owner

Documentation Curator Agent.

## Procedure

1. Read the handoff and identify its source-of-truth documents, decisions,
   assumptions, deviations, risks, and next step.
2. If `docs/` or an affected domain folder/index is missing, create it before
   inspecting and editing. Do not require a seeded project documentation tree.
   Otherwise, inspect the affected `docs/*/README.md` index before editing.
3. Add or update only documents with a clear reader, owner, and supported
   decision or workflow.
4. Update affected indexes, links, status, and supersession notes.
5. Put small review notes in the reviewed document and cross-domain reviews in
   `/docs/reviews/`.
6. Record contradictions instead of silently choosing between domain decisions;
   return ownership conflicts to the Studio Orchestrator, which must present the
   decision directly through OpenCode's `question` tool.
7. Check that paths use repository-relative Markdown links and that the result
   matches actual files and current decisions.

## Outputs

- Updated source-of-truth documents
- Updated affected folder README indexes
- Cross-links and supersession notes
- Review notes or a documented human decision request

## Exit criteria

- New or changed documents are discoverable from the relevant index.
- No stale links were introduced.
- Decisions, assumptions, risks, and human decisions remain distinguishable.
- The handoff records what was curated and what remains unresolved.
