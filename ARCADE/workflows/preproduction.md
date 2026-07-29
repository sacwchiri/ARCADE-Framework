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
- Which planned actions require image generation or engine MCP access?
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

- Create `docs/` and the required domain folders and `README.md` indexes on
  demand before writing the selected pre-production documents.
- `/docs/preproduction/preproduction-plan.md`
- `/docs/preproduction/prototype-plan.md`
- domain-specific docs in `/docs/design`, `/docs/art`, `/docs/ux`, `/docs/content`, `/docs/technical`, `/docs/audio`, `/docs/narrative`, or `/docs/levels`
- `/docs/validation/playtest-plan.md`
- `/docs/production/asset-manifest.md`
- capability verification report for any image-generation or engine-MCP action
- concept-art candidate artifacts and provenance when visual work is in scope
- folder README updates

## Exit criteria

- Highest-risk assumptions are identified.
- Prototype plan exists.
- Technical direction is clear enough to plan slices.
- Visual/UX/content needs are known enough for slice planning.
- Human has approved moving to production planning.
- Any art-bearing pre-production action has passed image-generation verification
  and produced concept-art candidates, or has an explicit human-approved skip.
- Any engine-dependent pre-production action has passed engine-MCP verification,
  or has a documented manual-engine step.

## Capability-aware routing

Classify each proposed pre-production action before delegation:

- Visual direction, character, environment, prop, UI mood, material, or other
  art-bearing work requires image-generation verification before the action starts.
- Multiplayer services, backend contracts, networking architecture, persistence,
  and other engineering-only work do not require image generation.
- Engine scene/prototype work requires engine-MCP verification only when it will
  actually use the engine MCP.

If image generation is required but unavailable, the Studio Orchestrator must
ask whether the human will configure it, explicitly skip it for that action, or
defer the action. A skip must be recorded in the pre-production handoff and
asset manifest; it is not an implicit pass.
