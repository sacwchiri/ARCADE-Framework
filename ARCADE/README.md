# ARCADE - Framework
## Agentic Roles for Collaborative Art, Development & Engineering

This pack defines a small-team, game-production-oriented agentic workflow for OpenCode.

It is designed for projects that move through four primary agent stages: concept, design, implement, and evaluate. Planning, integration, validation, and playtesting are delegated activities within those stages.

## Install

Copy the `.opencode` folder into your project root. It contains the agents,
commands, workflows, and OpenCode configuration:

```bash
cp -R .opencode /path/to/your/game-project/
```

The pack includes `.opencode/user-profile.default.yaml`, a general Solo Dev
fallback. Create `.opencode/user-profile.local.yaml` in the consuming project
for the local human's strengths, support needs, preferences, and ownership
expectations. The local file is ignored and should not be committed. Use
`/create-profile` to create it through a guided questionnaire.

The consuming project does not need a pre-created `docs/` folder. The first
workflow or subagent that needs project documentation creates the relevant
folders and README indexes on demand.

Start OpenCode from the consuming project root. Select the primary stage agent
that matches the work: `concept`, `design`, `implement`, or `evaluate`.
Project-specific agents live in `.opencode/agents/`, and the Markdown filename
becomes the agent name. Workflow source documents live in
`.opencode/workflows/`; executable slash commands live in `.opencode/commands/`.

## Choosing an agent

Start with the current stage of the work rather than with a specialist
discipline. The four primary agents own the user-facing workflow and normally
delegate to the smallest relevant specialist team.

| Primary agent | Use when | Main outcome |
| --- | --- | --- |
| `concept` | An idea, feature, system, visual direction, or technical question is still unclear. | A clear concept, pillars, scope boundaries, and next step. |
| `design` | Direction is approved but risks, requirements, architecture, content, assets, or prototypes still need planning. | An implementation-ready design and task plan. |
| `implement` | An approved task or slice is ready to build. | Scoped code, content, asset, or tooling changes with a handoff. |
| `evaluate` | A concept, prototype, slice, feature, bug, playtest, or release candidate needs an evidence-based decision. | A validation result and a recommendation to accept, iterate, ticket, or defer. |

### Direction and design specialists

These agents usually support `concept` or `design` rather than serving as the
first agent selected for an unclassified request.

| Agent | Suggested use |
| --- | --- |
| `director` | Game identity, player fantasy, pillars, product risks, scope, and human decision points. |
| `systems-designer` | Core loop, rules, player actions, state transitions, failure states, and progression. |
| `ux-designer` | Player flows, input, onboarding, accessibility, HUD states, and comprehension problems. |
| `content-designer` | Content taxonomy, quantities, progression categories, balance structure, and authoring rules. |
| `narrative-designer` | Worldbuilding, lore, canon, character or faction voice, naming, dialogue, and narrative progression. |
| `level-encounter-designer` | Maps, spaces, puzzles, encounters, spatial readability, pacing, and difficulty progression. |
| `art-director` | Visual identity, art pillars, references, readability, asset style, and visual consistency. |
| `audio-designer` | Audio identity, music direction, sound events, feedback, mix priorities, and audio requirements. |
| `technical-architect` | Architecture, runtime boundaries, networking, persistence, data ownership, content delivery, and technical risk. |
| `technical-art` | Import rules, shaders, materials, animation, VFX, asset contracts, and performance budgets. |
| `production-planner` | Approved direction into playable slices, milestones, dependencies, assignments, and definition of done. |
| `blind-spot-reviewer` | Hidden assumptions, scope traps, sequencing issues, technical risks, and validation gaps before a major decision. |

### Implementation specialists

These agents should normally be selected by `implement` or `production-planner`
after the task is approved and scoped.

| Agent | Suggested use |
| --- | --- |
| `prototype-implementation` | Clearly labeled, throwaway experiments that test an assumption. Promotion to production requires review and human approval. |
| `gameplay-implementation` | Approved gameplay rules, player actions, state machines, and game systems. |
| `backend-implementation` | Services, APIs, persistence, server-authoritative logic, telemetry, and backend tests. |
| `unity-client-implementation` | Unity client behavior, scenes, prefabs, presentation, and engine-facing code. |
| `ui-implementation` | Approved screens, HUDs, menus, UI states, and interface feedback behavior. It does not own gameplay rules. |
| `tools-implementation` | Editor tools, debug tools, import helpers, validators, and workflow automation. |
| `content-pipeline-implementation` | Schemas, loaders, validators, localization structures, and data workflows. It does not decide what content should exist. |
| `build-devops` | Build scripts, CI/CD, local environments, containers, deployments, and operational automation. |

### Implementation and support specialists

Use these as delegated capabilities within Implement or when a cross-cutting
workflow needs support. They do not silently change approved direction.

| Agent | Suggested use |
| --- | --- |
| `integration` | Connect parallel backend, client, gameplay, UI, content, asset, audio, tools, and documentation work into a playable slice. |
| `validation` | Test plans, sanity checks, playtest protocols, acceptance reports, regression checks, and tickets. It does not replace human judgments about fun or feel. |
| `code-quality-reviewer` | Read-only review of code structure, readability, compatibility, API boundaries, and test quality. |
| `art-integration` | Import and configure approved visual assets, prefabs, materials, sprites, icons, models, and placeholder replacements. |
| `audio-integration` | Wire approved audio events, music hooks, mix rules, and audio assets into the experience. |
| `vfx-integration` | Wire approved particles, shader effects, timing hooks, and feedback effects while preserving readability. |
| `tool-controller` | Use an approved external capability such as image generation or engine MCP through a verified adapter. It does not choose visual direction or approve assets. |
| `documentation-curator` | Maintain folder READMEs, links, decision traceability, reviews, superseded documents, and handoff clarity. |

### Profile agents

These are explicit workflow utilities, not general-purpose development agents.

| Agent | Suggested use |
| --- | --- |
| `profile-creator` | Create or revise the local collaboration profile through a guided questionnaire and explicit confirmation. |
| `profile-reviewer` | Compare the profile with repeated workflow evidence and propose updates without applying them silently. |

### Routing rules

- Use `concept` for uncertainty about what the game or feature should be.
- Use `design` for uncertainty about how an approved direction should become a plan.
- Use `implement` only after the task and scope are approved.
- Use `evaluate` when evidence or human judgment is needed before deciding what happens next.
- Let the primary agent delegate to specialists unless the specialist request is already concrete and approved.
- Use the smallest relevant specialist set; do not involve every discipline by default.
- Design agents decide what should exist. Implementation and integration agents build or connect it.
- Treat generated assets as candidates until a human approves their visual or audio direction.
- Keep decisions about fantasy, pillars, scope, taste, fun, feel, acceptance, and release readiness with the human.

The four primary agents are the lifecycle model. `design` handles concept
follow-through, risk reduction, prototypes, and slice planning. `implement`
handles approved work and its integration. `evaluate` handles validation,
playtesting, acceptance, and ticket recommendations. The repository
configuration uses `concept` as the default agent. Select `design`, `implement`,
or `evaluate` when the current work belongs to a later stage.

## User profile setup

After installation, run:

```text
/create-profile
```

The Profile Creator asks about the user's disciplines, strengths, guidance
needs, collaboration preferences, human ownership, and workflow defaults. It
shows a complete profile preview and writes the local profile only after
explicit confirmation.

Profile resolution is:

1. `.opencode/user-profile.local.yaml`
2. `.opencode/user-profile.default.yaml`

The local profile is ignored by Git and is specific to the human working on the
project. If it does not exist, ARCADE uses the general Solo Dev default. Run
`/review-profile` later to compare repeated workflow evidence with the profile
and receive proposed updates. Profile review never changes the file silently.

Profiles affect guidance, discipline routing, questions, output format, and
review emphasis. They do not change permissions, approved scope, human approval
gates, or project authority.

## Core idea

Agents do not merely build features. They transform uncertainty into decisions, decisions into playable slices, slices into integrated experiences, and human observations into better design, assets, code, documentation, and tickets.

## Human authority

Humans remain responsible for:

- final creative direction
- game pillars
- taste and fun judgments
- slice approval
- playtest interpretation
- major scope changes
- release readiness

Agents can recommend, draft, implement, validate, and challenge, but they should not silently decide human-owned matters.
