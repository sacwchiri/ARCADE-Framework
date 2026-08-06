# Workflow: Production Execution

Use this workflow when approved tasks are ready to be implemented.

## Goal

Build approved tasks without changing product direction, architecture, or scope without escalation.

## Default agents

Selected by Production Planner:

- Prototype Implementation Agent
- Gameplay Implementation Agent
- Backend Implementation Agent
- Unity Client Implementation Agent
- UI Implementation Agent
- Tools Implementation Agent
- Content Pipeline Implementation Agent
- Build/DevOps Agent
- Art Integration Agent
- Audio Integration Agent
- VFX Integration Agent
- Tool Controller Agent, only after the action is classified and the required
  capability has passed tooling verification

Supporting agents:

- Integration Agent
- Validation Agent
- Documentation Curator Agent

## Required behavior

Implementation agents must:

1. Read the approved task.
2. Read relevant docs.
3. Inspect existing code/content/assets.
4. Produce a short implementation plan.
5. Edit only approved scope.
6. Run available checks.
7. Produce a handoff.

Before delegation, the Implement stage agent classifies each approved task. Image
generation is required for art-bearing tasks and skipped for engineering-only
tasks. Engine MCP verification is required only for tasks that use engine MCP.
Missing capabilities pause the task for a configure, skip, or defer decision.
The task's preferred discipline, when present, and the resolved user profile may
influence specialist selection and explanation depth, but not permissions or
capability verification.

## Human interactions required

Return these decisions to the Implement stage agent. It must present them
directly through OpenCode's `question` tool and pause execution until answered:

- implementation requires changing approved behavior
- task scope is ambiguous
- final visual/audio/feel quality requires taste approval
- prototype code is proposed for production promotion

## Outputs

- code/content/assets/tooling changes
- implementation handoffs
- integration notes
- documentation updates; create any required `docs/` domain folder and
  `README.md` index before writing new project documentation
- validation recommendations

## Exit criteria

- Implementation handoff exists.
- Integration requirements are documented.
- Validation knows what to check.
- Documentation Curator has updated affected READMEs/docs if needed.
