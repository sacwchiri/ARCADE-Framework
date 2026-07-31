# Workflow: Tooling Verification

Use this workflow immediately before an approved action that requires image
generation or game-engine MCP access.

## Goal

Prove that the capability needed by the next action is configured and usable,
without running unrelated tools or changing project scope.

## Procedure

1. Read the approved action and classify it using
   `protocols/capability-verification.md`.
2. If the action is `art-independent` and `engine-independent`, record that no
   external capability is required and continue without verification.
3. For `image-generation`, ask Tool Controller to verify the approved image
   provider and perform a minimal smoke generation when no current verification
   exists.
4. For `engine-mcp`, ask Tool Controller to verify the configured engine MCP
   and perform a harmless read-only connectivity check.
5. Do not load or probe unrelated providers or MCP servers.
6. If a check fails, pause for the human decision defined by the capability
   verification protocol.
7. Store the report and return it to the requesting workflow before the action
   begins.

## Required human interactions

The active stage agent must ask directly through `question` when:

- image generation is required but no provider is configured;
- engine MCP is required but unavailable;
- the human wants to skip generation or defer engine access;
- verification would require paid, batch, destructive, or irreversible work.

## Outputs

- capability verification report or explicit no-capability result;
- image smoke-test artifact and provenance handoff when applicable;
- engine MCP connectivity result when applicable;
- recorded configure, skip, or defer decision;
- next-step handoff to the requesting workflow.

## Exit criteria

- Every capability required by the next action has passed, or
- the human has explicitly approved a documented skip/defer path.
