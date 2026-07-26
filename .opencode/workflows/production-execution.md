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
- Tool Controller Agent, only when an approved external tool capability is needed

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

## Human interactions required

Ask humans when:

- implementation requires changing approved behavior
- task scope is ambiguous
- final visual/audio/feel quality requires taste approval
- prototype code is proposed for production promotion

## Outputs

- code/content/assets/tooling changes
- implementation handoffs
- integration notes
- documentation updates
- validation recommendations

## Exit criteria

- Implementation handoff exists.
- Integration requirements are documented.
- Validation knows what to check.
- Documentation Curator has updated affected READMEs/docs if needed.
