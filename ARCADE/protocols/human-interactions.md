# Protocol: Human Interactions

This workflow is designed for a small team where humans remain the creative owner, taste judge, and final approver.

## Human-owned decisions

Humans approve:

- game pillars
- core fantasy
- target audience
- platform and scope changes
- visual direction
- final quality/taste of art, UI, audio, and feel
- production slice count and order
- whether a prototype should continue
- whether playtest results imply pivot, iteration, or acceptance
- major architecture tradeoffs when cost/scope is significant
- release readiness

## Agent-owned decisions

Agents may decide:

- how to structure a draft document
- which documents appear necessary, within their domain
- recommended technical approaches
- proposed production slices
- suggested task breakdowns
- validation plans
- ticket formatting
- documentation organization

Agents recommend. Humans approve when the decision affects direction, scope, taste, or long-term cost.

## Required question style

When human input is needed, ask concrete questions.

## Direct questionnaire rule

Human decisions must use two channels:

1. Record the question and its current status in the relevant source-of-truth
   document or handoff.
2. The Studio Orchestrator must present the unresolved question directly through
   OpenCode's `question` tool.

Writing a question into `open-questions.md`, a review note, or a handoff is not
enough. The workflow must pause until the orchestrator receives an answer.

Specialist agents must return human questions to the orchestrator in their
handoff. They must not treat a documented question as answered, and the
orchestrator must not advance the workflow while a required decision is pending.

Use these decision states:

- `Pending`: identified but not yet answered.
- `Approved`: human accepted the proposal.
- `Approved with changes`: human accepted the direction subject to requested edits.
- `Rejected`: human declined the proposal or asked for a different direction.
- `Not applicable`: the decision no longer applies, with a reason recorded.

For each direct questionnaire item, provide the relevant context, a concise
question, concrete options where possible, and a free-text option for requested
changes. After receiving an answer, record it in the relevant document and
handoff before continuing.

Good:

- Should multiplayer be proven before or after the local core loop?
- Is the visual target closer to low-poly toy board game or divine casino table?
- Is this slice too large for the first playable milestone?

Bad:

- What do you think?
- Any feedback?
- Should we improve this?

## Human playtesting

Agents can prepare playtest plans and convert findings into tickets. Humans judge fun, feel, pacing, clarity, and taste.
