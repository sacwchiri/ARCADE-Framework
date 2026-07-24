---
description: Evaluate a named or numbered slice and record its technical evidence and human acceptance decision.
agent: evaluate
---

Read `.opencode/protocols/stage-entry.md`,
`.opencode/protocols/human-interactions.md`,
`.opencode/workflows/validation.md`, and
`.opencode/workflows/documentation-curation.md`.

Evaluate the requested slice:
$ARGUMENTS

Resolve the slice source-of-truth document from `docs/production/`, inspect the
implementation handoff, run available checks, and separate tool-checkable
results from human judgments. Create or update the per-slice report at
`docs/validation/acceptance-reports/slice-$ARGUMENTS.md` when the argument is a
number; use the normalized slice name for a named argument. Update the relevant
validation and production indexes, preserving existing decisions and evidence.

Do not mark the slice accepted from automated checks alone. Ask the human
directly for one of `Approved`, `Approved with changes`, `Rejected`, or `Not
applicable`, record the answer, and only then recommend the next workflow.
