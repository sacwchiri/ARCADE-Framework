# Game development agentic workflow guides

This pack defines a small-team, game-production-oriented agentic workflow for OpenCode.

It is designed for projects that start from a general game idea and need to move through concept, pre-production, production planning, implementation, integration, validation, and human playtesting.

## Install

Copy the `.opencode` folder into your project root:

```bash
cp -R .opencode /path/to/your/game-project/
```

OpenCode project-specific agents live in `.opencode/agents/`. The Markdown filename becomes the agent name.

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
