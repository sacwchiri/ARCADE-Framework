# Workflow: Integration

Use this workflow when parallel work needs to become an end-to-end playable experience.

## Goal

Verify that all parts connect correctly.

## Default agents

- Integration Agent
- Technical Architect Agent
- Systems Designer Agent
- UX Designer Agent
- Technical Art Agent
- Audio Designer Agent, if audio is involved
- Validation Agent
- Documentation Curator Agent

## Contracts to check

- Backend ↔ client API
- Gameplay ↔ UI events
- Content schema ↔ gameplay logic
- Asset contracts ↔ Unity/prefab integration
- Audio events ↔ gameplay/UX triggers
- UX state contract ↔ implementation
- Production tasks ↔ actual deliverables

Before checking engine-side contracts, verify `engine-mcp` when the integration
action uses the engine MCP. Art-independent integration must not trigger image
generation. Art-bearing integration must have a prior image-generation report
or an explicit human-approved skip.

## Human interactions required

Return these decisions to the Implement stage agent. It must present them
directly through OpenCode's `question` tool and pause integration until answered:

- an integration mismatch exposes an ownership conflict
- the result works technically but feels wrong
- accepting the slice requires a taste/fun decision

## Outputs

- Create `docs/` and the required production, validation, or contract-domain
  folders and `README.md` indexes on demand before recording results.
- `/docs/production/integration-report.md`
- `/docs/validation/integration-checklist.md`
- tickets for integration failures
- updated contracts if approved

## Exit criteria

- End-to-end path is checked.
- Mismatches are resolved or ticketed.
- Human-facing result is ready for validation/playtest.
