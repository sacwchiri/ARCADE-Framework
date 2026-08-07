# Protocol: Stage Entry

Stage agents are selectable primary entry points. They own the work for their
stage and may delegate to the smallest relevant specialist team. No stage agent
may silently advance the work into another stage.

## Intake

Before delegating, identify:

- work type: project, system, feature, task, bug, research, or playtest finding
- current stage and requested outcome
- existing source-of-truth documents, code, content, and assets
- decisions already approved
- assumptions, risks, constraints, and missing information
- required tools and whether they are available
- resolved local or default user profile
- explicit or inferred task discipline

For an established project, prefer the existing ticket, design document, code,
and project conventions over creating generic project-level artifacts.

## Alignment loop

When the human asks for exploration, comparison, or alignment rather than final
execution:

1. Produce one or more clearly differentiated proposals.
2. Identify tradeoffs, risks, open questions, and a recommendation.
3. Ask concrete human questions through OpenCode's `question` tool.
4. Record the answer and requested changes in the relevant source-of-truth
   document or handoff.
5. Revise only after the answer is received.

Do not create an indefinite loop. Every iteration ends with a recommendation,
an explicit decision request, or a clear reason that work is blocked.

The user profile may adapt guidance depth, questions, routing, and output format.
It may not change stage boundaries, permissions, approved scope, human authority,
capability verification, or the definition of done. Load the profile once at the
primary stage and pass only a compact relevant context capsule to subagents.

If the human does not know the answer, offer a default and mark it as an
assumption pending validation.

## Human gates

Pause for human approval when work changes direction, pillars, scope,
architecture, visual or feel quality, acceptance, prototype promotion, or the
meaning of playtest results. Use the decision states from
`human-interactions.md`: `Pending`, `Approved`, `Approved with changes`,
`Rejected`, and `Not applicable`.

## Stage boundaries

- Concept clarifies direction, pillars, scope, and open questions. It may
  recommend Design, but does not create implementation tasks as if the
  direction were approved.
- Design prepares requirements, technical plans, prototypes, asset
  requirements, coding conventions, validation plans, and slices, but does not
  implement production code.
- Implement consumes an approved task or plan and owns implementation and
  integration. It does not change behavior, architecture, scope, or quality
  targets without escalation.
- Evaluate owns validation, playtesting, acceptance, ticketing, and iteration
  recommendations. It may accept, reject, ticket, or recommend returning to
  Concept, Design, or Implement. It does not silently fix failed work while
  evaluating it.

## Handoff

Every stage handoff identifies:

- source-of-truth documents
- changed files or assets
- decisions and assumptions
- deviations and risks
- pending human decisions
- recommended next stage or loop
