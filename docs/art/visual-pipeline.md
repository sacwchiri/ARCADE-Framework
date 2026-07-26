# Visual Pipeline

## Purpose

Defines how artist-created, generated, procedural, and licensed visual assets
move from an approved request into the game.

## Asset paths

- Artist-created: source work is reviewed against the visual direction and asset contract.
- Generated: tools create candidates; a human selects and an artist or Technical Art cleans them up.
- Procedural: scripts or authoring tools create repeatable output with recorded parameters.
- Licensed: an external asset is checked for license, fit, and technical constraints.
- Kitbashed: combined sources retain provenance for each contributing asset.

All paths converge on the same source, export, preview, provenance, validation,
and approval requirements.

## Standard flow

1. Art Director or UX Designer defines the approved visual intent.
2. Production adds the asset request to the slice and asset manifest.
3. Tool Controller is invoked only if a registered capability is needed.
4. Candidates are stored separately from runtime exports.
5. Human selects or rejects candidates when direction or taste is affected.
6. Technical Art checks constraints and provenance.
7. Art Integration imports the approved candidate and creates runtime content.
8. Validation checks technical and acceptance requirements.
9. Human approves final visual quality.

## Required separation

- Concept art is reference until explicitly promoted.
- Generated output is a candidate until reviewed.
- Source files are not runtime files.
- Technical validation is not taste approval.
- Placeholder assets remain replaceable.
