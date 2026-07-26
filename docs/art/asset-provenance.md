# Asset Provenance

This document defines the project-facing record for external and generated
assets. The field-level rules live in
`.opencode/protocols/asset-provenance.md`.

## Record template

```markdown
Asset: [asset ID]
Revision: [revision]
Source type: artist | generated | procedural | licensed | kitbashed
Source file: [path]
Runtime export: [path]
Tool/provider/library: [name]
Model/version: [if applicable]
Prompt/source reference: [if useful]
Input assets: [paths or IDs]
License: [license and attribution]
Commercial use: [allowed, restricted, or unresolved]
Human editor/approver: [name or role]
Date: [date]
Restrictions/open questions: [notes]
```

Unresolved licensing or provenance questions block production promotion.
