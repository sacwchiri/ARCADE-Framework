# Workflow: Profile Creation

Use this workflow to create or revise the local user profile for the human
working on the consuming project.

## Goal

Create `.opencode/user-profile.local.yaml` through a guided questionnaire and
explicit human confirmation. The profile adapts collaboration guidance and
routing; it does not change project authority, permissions, or workflow gates.

## Profile source

1. Read `.opencode/user-profile.default.yaml` as the schema and safe baseline.
2. If `.opencode/user-profile.local.yaml` exists, offer to review it, replace it
   after confirmation, or cancel.
3. Never modify the default profile.

## Questionnaire rounds

Ask concise, grouped questions through the `question` tool. Do not ask the user
to edit YAML directly.

### Identity and context

- Optional display name or identifier.
- Whether the user is working as a solo developer, team contributor, or hybrid
  contributor.

Record this as `user.working_context` using `solo_dev`, `team_contributor`, or
`hybrid_contributor`.

### Disciplines

Ask which disciplines the user actively contributes to. For each selected
discipline, ask for strength and guidance need. Use `unknown` or `adaptive` when
the user is unsure. Strength and guidance need are independent.

Supported baseline disciplines:

- engineering
- art_2d
- art_3d
- technical_art
- design
- production
- validation

Additional disciplines may be recorded only when they improve routing for the
current project.

### Collaboration preferences

Ask about:

- technical explanation depth;
- cross-discipline support;
- concise, detailed, or adaptive explanations;
- reusable solutions versus rapid prototypes;
- visual variations versus final generated art.

### Human ownership

Ask which areas need explicit human review. Ownership settings may add review
requirements but may not remove global human approval gates.

Supported values:

- `human`
- `agent_recommendation`
- `collaborative`
- `delegated_with_review`

### Workflow defaults

Ask for the default discipline and whether to require blind-spot and profile
review suggestions. Task-level discipline preferences still take precedence.

## Preview and confirmation

After the questionnaire:

1. Generate a complete profile preview.
2. Summarize how guidance, routing, questions, and review emphasis will change.
3. Ask the human to choose `Create`, `Revise`, or `Cancel`.
4. Write the local profile only after `Create`.

If the human chooses `Revise`, ask only the relevant unanswered or changed
questions. If the human chooses `Cancel`, leave the existing profile unchanged
and use the default or existing local profile.

## Output constraints

- Write only `.opencode/user-profile.local.yaml`.
- Preserve `schema_version`.
- Start new profiles with `observations: []`.
- Do not invent strengths, preferences, or ownership decisions.
- Do not update project documentation as part of profile creation.
- Do not silently overwrite an existing local profile.

## Completion

Report:

- profile source created or updated;
- disciplines and guidance needs recorded;
- preferences recorded;
- ownership and review requirements recorded;
- fallback behavior if creation was cancelled;
- recommended next step: begin the relevant workflow or run `/review-profile`
  after meaningful work.
