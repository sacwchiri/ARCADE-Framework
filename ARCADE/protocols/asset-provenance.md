# Protocol: Asset Provenance

Every external, generated, procedural, or kitbashed asset must have a
discoverable provenance record before it can become `Ready for integration`.

## Required fields

- Asset ID and revision
- Source type: artist, generated, procedural, licensed, or kitbashed
- Source file and runtime export
- Tool, provider, or library
- Model/version when applicable
- Prompt or source reference when useful for reproduction
- Input assets and licenses
- Commercial-use and attribution requirements
- Human editor or approver
- Date
- Known restrictions or unresolved questions

## Rules

- `Generated` is not an approval state.
- Unclear licensing blocks production promotion.
- Provenance must travel with the asset manifest and integration handoff.
- Do not store secrets or private API credentials in provenance records.
