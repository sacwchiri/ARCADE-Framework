# Protocol: Tool Routing

External tools are capabilities, not default context for every agent.

## Routing rules

- The orchestrator identifies whether a tool capability is needed.
- The Tool Controller loads one relevant registry entry at a time.
- Provider-specific instructions remain inside the adapter or MCP.
- Credentials and project-specific MCP configuration stay in the consuming game
  project, never in this workflow pack.
- Prefer an existing approved artifact over creating a new one.
- Prefer dry-run for paid, batch, destructive, or irreversible actions.
- Verify a required capability immediately before invocation; do not run a
  blanket check for unrelated providers or MCP servers.
- Tool selection must account for license, cost, output format, latency, and
  technical suitability.
- A tool result is an artifact handoff, not a replacement for human approval.

## Context rules

- Do not include full API responses, binary data, or provider documentation in
  agent context.
- Store large outputs at artifact paths and return previews or summaries.
- Pass artifact IDs, manifest paths, and validation results to later agents.
- Cache outputs as files and metadata, not as repeated prompt text.

## Tool registry entry

Each registered capability should identify:

- Capability name
- Approved adapter or provider
- Input contract
- Output contract
- Enabled status
- Authentication requirement
- Cost and latency characteristics
- License or provenance risk
- Destructive-operation risk
- Fallback capability
- Owner

## Capability classification

Before routing, classify the action as `image-generation`, `engine-mcp`,
`art-independent`, `engine-independent`, or a combination. Use
`capability-verification.md` for required checks and missing-capability decisions.
