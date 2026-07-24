# Workflow: Validation

Use this workflow to check concepts, prototypes, slices, features, bugs, and release candidates.

## Goal

Determine whether work satisfies design, technical, production, and player-experience goals.

## Default agents

- Validation Agent
- Integration Agent
- Blind Spot Reviewer Agent, for review gates
- Documentation Curator Agent

## Validation types

- Design validation
- Technical validation
- QA sanity check
- Asset validation
- Playtest validation
- Regression validation
- Release validation

## Human interactions required

Humans must judge:

- fun
- feel
- pacing
- clarity
- confusion
- social tension
- visual/audio taste
- whether the slice should be accepted

Agents should convert human findings into tickets when needed.

## Outputs

- `/docs/validation/test-plan.md`
- `/docs/validation/playtest-plan.md`
- `/docs/validation/playtest-sessions/*.md`
- `/docs/validation/acceptance-report.md`
- `/docs/production/tickets/*.md`

## Exit criteria

- What passed is documented.
- What failed is documented.
- Human-only judgments are separated from tool-checkable results.
- Issues are ticketed.
- Acceptance status is clear.
