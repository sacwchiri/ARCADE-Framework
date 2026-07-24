# Workflow: Production Planning

Use this workflow to turn approved concept/pre-production decisions into playable slices, milestones, and implementation tasks.

## Goal

Create a production plan that describes how to accomplish the proposal.

## Required slice rule

Every slice must include minimum playable experience layers:

- design
- gameplay/code
- UX/UI
- art/assets or placeholders
- audio/VFX or placeholders when relevant
- content
- integration
- validation
- documentation

A slice is not complete just because code exists.

## Default agents

- Production Planner Agent
- Director Agent
- Systems Designer Agent
- Art Director Agent
- UX Designer Agent
- Content Designer Agent
- Technical Architect Agent
- Technical Art Agent
- Integration Agent
- Validation Agent
- Blind Spot Reviewer Agent
- Documentation Curator Agent

## Required human slice validation

Before final task breakdown, ask:

1. Are there too many or too few slices?
2. Should any slice happen earlier?
3. Should any slice be merged, split, or removed?
4. Is the first slice the correct first playable target?
5. Is there a technical, visual, content, or UX risk that should be moved earlier?

## Outputs

- `/docs/production/slices.md`
- `/docs/production/milestones.md`
- `/docs/production/task-breakdown.md`
- `/docs/production/dependencies.md`
- `/docs/production/asset-manifest.md`
- `/docs/production/definition-of-done.md`

## Exit criteria

- Human has approved slice count and order, or explicitly accepted agent recommendations.
- First slice is clear.
- Specialty agents are assigned.
- Dependencies are known.
- Validation checkpoints are defined.
