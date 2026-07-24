# Workflow: Profile Review

Use this workflow to compare the local user profile with repeated evidence from
recent work. It proposes changes; it does not silently update the profile.

## Goal

Identify whether guidance, routing, or collaboration preferences no longer match
the user's observed needs.

## Evidence

Use only concrete evidence such as:

- repeated requests for more or less explanation;
- repeated routing overrides;
- repeated corrections in the same discipline;
- repeated rejection of an output type;
- explicit user statements about a changed preference.

Do not infer a stable preference from one unusual task. Distinguish task-specific
needs from repeated project-wide patterns.

## Procedure

1. Resolve the local or default profile.
2. Inspect recent handoffs, task documents, review notes, and explicit user
   corrections when available.
3. Identify patterns and count supporting evidence.
4. Compare each pattern with the declared profile.
5. Propose profile changes with confidence and evidence.
6. Ask the human whether to accept, reject, defer, or record the suggestion.

## Observation format

```yaml
- date: YYYY-MM-DD
  area: technical_art
  signal: repeated_asset_pipeline_explanations
  evidence_count: 3
  confidence: medium
  suggestion: increase_technical_art_guidance
  status: pending
```

Accepted changes require explicit human confirmation. Rejected suggestions may
remain as historical observations but must not be treated as active preferences.

## Output

- Active profile source
- Evidence reviewed
- Confirmed patterns
- Suggested changes
- Confidence and evidence count
- Human decisions needed
- Recommended next review point
