# Protocol: Capability Verification

Capability verification confirms that a required external capability is
configured and usable immediately before work invokes it. It is not a general
project health check and it does not approve visual quality or promote assets.

## Capability classes

- `image-generation`: concept art, visual references, generated candidates, or
  any art request whose output must be created by an image provider.
- `engine-mcp`: engine scene edits, asset import, prefab/material setup, or
  engine-side validation.
- `art-independent`: design, architecture, backend, networking, service, or
  documentation work with no visual artifact requirement.
- `engine-independent`: work that does not need an engine MCP connection.

An action may have both required capabilities. Classify the action before
delegating it; do not infer a capability from the overall workflow stage.

## Verification checks

### Image generation

- A project registry entry identifies an approved provider or adapter.
- The provider is enabled and authorized without exposing credentials.
- A minimal smoke generation succeeds, or a recent valid verification is still
  current and tied to the same provider configuration.
- The result has an artifact path or ID, preview, and provenance handoff.
- The smoke output remains a candidate and is never silently promoted.

### Engine MCP

- The consuming project declares an enabled engine MCP server.
- The server configuration is syntactically usable without printing secrets.
- A harmless read-only connectivity or capability check succeeds.
- The result identifies the engine/project context and the next permitted action.

## Missing capability

If a required capability is unavailable, pause and ask the human through the
Active stage agent questionnaire:

1. Configure or enable the required capability.
2. Skip the capability for this action.
3. Stop or defer the action.

Skipping image generation requires an explicit record in the handoff and asset
manifest. The action may use references or placeholders only where the approved
scope permits them. Skipping engine MCP requires a documented manual-engine
step or a scope change; it must not be treated as a successful engine check.

## Verification report

Return a compact report containing:

- Request and action ID
- Classified capabilities
- Checks performed and timestamp
- Provider/MCP identity and enabled status, not credentials
- Artifact or connectivity result
- Failure, skip, or defer decision
- Human decision required
- Recommended next step

Store large tool output as artifacts. Do not put binary image data, API
responses, tokens, or private MCP configuration in the report.
