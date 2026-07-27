# Workflow: Art Pipeline

Use this workflow when a slice needs concept art, models, textures, materials,
UI assets, visual references, or generated/artist-created asset candidates.

## Goal

Move an art request from a structured brief to a reviewed, technically valid,
and integration-ready asset without exposing every external tool to every
agent.

## Ownership

- Art Director owns visual direction and taste approval.
- UX Designer owns UI behavior, states, and comprehension.
- Technical Art owns asset constraints, import rules, and validation criteria.
- Tool Controller owns external tool selection and invocation.
- Art Integration owns engine import, prefabs, materials, and runtime setup.
- Validation owns technical and acceptance checks.
- Humans approve direction, quality, licensing exceptions, and promotion.

## Procedure

1. Read the approved slice, visual direction, UX contract, and asset manifest.
2. Create or update a structured asset request with purpose, references, type,
   constraints, variants, target platform, and approval requirements.
3. Determine whether the request needs an artist, a licensed existing asset, a
   procedural tool, an external generator, or a combination.
4. Ask the Tool Controller for a capability only when an external or local
   authoring tool is required. Do not load unrelated tools.
5. Produce candidates or source assets. Keep source files separate from runtime
   exports and record provenance immediately.
6. Ask the Art Director or UX Designer to select or reject candidates when the
   output affects visual direction, UI mood, or player comprehension. Return any
   human decision to the Studio Orchestrator for direct questionnaire handling.
7. Ask Technical Art to check the asset contract and runtime constraints.
8. Send accepted candidates to Art Integration for engine import and setup.
9. Run validation and update the asset manifest status.
10. Return direction, quality, licensing exceptions, and promotion decisions to
    the Studio Orchestrator. It must ask them directly through OpenCode's
    `question` tool and record approval before marking final visual quality as
    Approved.

## Asset state rules

`Generated` means a tool produced an output. It does not mean the asset is
usable, licensed, technically valid, or approved. Use `Ready for integration`
only after the asset contract and provenance checks pass.

## Exit criteria

- Asset request exists and is linked to the slice.
- Source, runtime export, preview, and provenance are identifiable.
- Technical constraints and validation results are recorded.
- Human visual or UX approval is recorded where required.
- The asset manifest has a current status, owner, and next step.
