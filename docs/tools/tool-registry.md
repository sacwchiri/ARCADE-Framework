# Tool Registry

The registry describes capabilities, not a permanently loaded list of tools.
The Tool Controller reads only the entry needed for the current request.

## Registry entry template

```markdown
Capability: [capability name]
Approved adapter/provider: [name]
Enabled: yes | no | project decision
Input contract: [request shape]
Output contract: [artifact shape]
Authentication: [requirement]
Cost/latency: [notes]
License/provenance risk: [notes]
Destructive-operation risk: [none, low, medium, high]
Fallback: [capability or none]
Owner: [role]
```

## Initial capabilities

### Concept image generation

- Input: structured art request, references, aspect ratio, and variant count.
- Output: preview images plus provenance record.
- Human approval: required before use as visual direction or production source.
- Risk: provider terms, style inconsistency, source-image restrictions, and usage cost.

### 3D authoring and export

- Input: model brief, references, topology budget, scale, and export target.
- Output: source scene, runtime export, preview, and technical report.
- Human approval: required for visual direction and production promotion.
- Risk: topology, UVs, rigging, material compatibility, and licensing.

### Material generation

- Input: material brief, map requirements, resolution, and shader target.
- Output: source material, texture maps, metadata, and preview.
- Human approval: required when the material establishes visual direction.
- Risk: color space, compression, shader compatibility, and texture size.

### UI design and export

- Input: screen/state contract, design references, tokens, and export formats.
- Output: source design, exported assets, and state preview.
- Human approval: required for readability, hierarchy, and final feel.
- Risk: scaling, localization, accessibility, and inconsistent states.

### Engine asset validation

- Input: asset path, asset contract, and target platform constraints.
- Output: validation report and suggested fixes.
- Human approval: not required for a pass/fail report; required for exceptions.
- Risk: false confidence if the contract is incomplete.

## Project-specific entries

Add enabled providers and adapters in the consuming game project's registry or
configuration. Do not commit secrets here.
