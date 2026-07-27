# Workflow: Pre-production

Use this workflow when a concept is promising but still has uncertainty.

## Goal

Reduce uncertainty and prepare for production planning.

Pre-production asks:

- What must be proven?
- What documents are needed?
- What prototypes are needed?
- What architecture is needed?
- What content and asset pipeline is needed?
- What are the largest risks?

## Default agents

- Director Agent
- Systems Designer Agent
- Art Director Agent
- UX Designer Agent
- Content Designer Agent
- Technical Architect Agent
- Technical Art Agent
- Audio Designer Agent, if audio feedback matters
- Narrative Designer Agent, if lore/voice matters
- Level/Encounter Designer Agent, if authored spaces or encounters matter
- Blind Spot Reviewer Agent
- Production Planner Agent
- Validation Agent
- Documentation Curator Agent

## Required human interactions

Return these decisions to the Studio Orchestrator. The orchestrator must ask
them directly through OpenCode's `question` tool and record the answers in the
source-of-truth documents:

- Which risks must be proven first?
- Which prototype results feel good enough?
- Which visual direction should be pursued?
- Which content scope is realistic?
- Which technical tradeoff is acceptable?
- Is the project ready for production planning?

## Outputs

- `/docs/preproduction/preproduction-plan.md`
- `/docs/preproduction/prototype-plan.md`
- domain-specific docs in `/docs/design`, `/docs/art`, `/docs/ux`, `/docs/content`, `/docs/technical`, `/docs/audio`, `/docs/narrative`, or `/docs/levels`
- `/docs/validation/playtest-plan.md`
- `/docs/production/asset-manifest.md`
- folder README updates

## Exit criteria

- Highest-risk assumptions are identified.
- Prototype plan exists.
- Technical direction is clear enough to plan slices.
- Visual/UX/content needs are known enough for slice planning.
- Human has approved moving to production planning.
