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

Each task must also declare its capability requirements. Art-bearing tasks route
through concept-art/image-generation verification before generation;
engineering-only tasks must not acquire or generate art as a side effect. Engine
tasks declare `engine-mcp` only when they actually require engine MCP.

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

Before final task breakdown, return these questions to the Studio Orchestrator.
It must present them directly through OpenCode's `question` tool and record the
answers before finalizing the task breakdown:

1. Are there too many or too few slices?
2. Should any slice happen earlier?
3. Should any slice be merged, split, or removed?
4. Is the first slice the correct first playable target?
5. Is there a technical, visual, content, or UX risk that should be moved earlier?

## Outputs

- Create `docs/` and the required production/domain folders and `README.md`
  indexes on demand before writing the plan.
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
