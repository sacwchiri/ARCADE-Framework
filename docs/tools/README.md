# Tool Documentation

This folder describes external tool capabilities and their controlled use in
the game workflow. It does not contain credentials or project-specific MCP
configuration.

## Primary owner

- Tool Controller Agent

## Supporting agents

- Technical Art Agent
- Tools Implementation Agent
- Art Integration Agent
- Documentation Curator Agent

## Current documents

| Document | Purpose | Status | Owner |
|---|---|---|---|
| README.md | Explains the purpose and current document map. | Active | Documentation Curator Agent |
| [tool-registry.md](tool-registry.md) | Defines capability-oriented external tool entries and routing metadata. | Active | Tool Controller Agent |

Capability checks are performed immediately before an action needs image
generation or game-engine MCP. Engineering-only actions do not trigger image
generation. Provider credentials and MCP definitions remain in the consuming
project.

## Configuration boundary

The consuming game project owns actual MCP server definitions, API keys,
provider settings, and enabled-tool choices. This pack owns routing contracts,
approval rules, and handoff formats.
