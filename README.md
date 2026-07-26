# ARCADE - Framework
## Agentic Roles for Collaborative Art, Development & Engineering

This pack defines a small-team, game-production-oriented agentic workflow for OpenCode.

It is designed for projects that start from a general game idea and need to move through concept, pre-production, production planning, implementation, integration, validation, and human playtesting.

## Install

Copy the `.opencode` folder and `opencode.json` into your project root:

```bash
cp -R .opencode /path/to/your/game-project/
cp opencode.json /path/to/your/game-project/
```

Start OpenCode from the consuming project root. The Studio Orchestrator is the
default primary agent. Project-specific agents live in `.opencode/agents/`, and
the Markdown filename becomes the agent name. Workflow source documents live in
`.opencode/workflows/`; executable slash commands live in `.opencode/commands/`.

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
