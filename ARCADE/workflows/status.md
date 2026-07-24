# Workflow: Status

Use this workflow to determine which primary agent should handle the current
work and what should happen next.

## Goal

Give the human a short, evidence-based status report without creating or changing
project decisions.

## Procedure

1. Inspect the relevant `docs/*/README.md` indexes and current project
   documents. If `docs/` is missing, report the project as documentation
   uninitialized and continue without creating files.
2. Check for concept, design, implementation, evaluation, ticket, and
   documentation records. Treat planning, integration, and validation records
   as evidence within those primary stages, not as separate stages.
3. Identify the latest approved decision and any explicit human gate still open.
4. Report missing evidence separately from confirmed state.
5. Recommend exactly one next workflow. When the next step depends on an
   unresolved decision, return one concrete question to the active stage agent,
   which must present it directly through OpenCode's `question` tool.

## Output

- Current workflow state
- Evidence and source documents
- Completed gates
- Open human decisions
- Risks or missing records
- One recommended next step

## Constraints

This is a read-only assessment. Do not infer approval from the existence of a
draft document, and do not modify project files unless the human starts the
recommended workflow afterward.
