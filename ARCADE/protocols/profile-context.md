# Protocol: User Profile Context

The user profile describes the human working on the project. It is a local
collaboration context, not an agent variant, staffing plan, permission profile,
or replacement for workflow stages.

## Profile resolution

Resolve profiles in this order:

1. `.opencode/user-profile.local.yaml`
2. `.opencode/user-profile.default.yaml`

The local profile is ignored by the repository and must not be committed. If no
profile is available, use the default profile and report that the fallback is
active when it affects the recommendation.

Create or revise the local profile with `/create-profile`. The creator asks
grouped questions, shows a complete preview, and writes the local file only
after explicit human confirmation. It never modifies the default profile.

The profile may record `user.working_context` as `solo_dev`,
`team_contributor`, or `hybrid_contributor`. This describes the human's project
context and does not change required disciplines or approval gates.

## Precedence

When context conflicts, use this order:

1. Direct human instruction
2. Approved task, design, and project decisions
3. ARCADE workflow and authority protocols
4. Task-level discipline or guidance override
5. Active user profile
6. Agent defaults

The profile may change guidance, routing, questions, output format, and review
emphasis. It must not change permissions, human approval gates, capability
verification, approved scope, or the definition of done.

## Task discipline

Tasks may declare an optional preferred discipline or list of disciplines:

```yaml
preferred_discipline: engineering
preferred_disciplines:
  - gameplay
  - technical_art
```

Use explicit task preferences first. If absent, recommend a discipline from the
task and profile, then fall back to the profile's default discipline. Record the
resolved discipline in the handoff when it affects routing.

## Primary agent procedure

The active primary stage agent should:

1. Load the resolved profile once.
2. Identify the task's preferred or inferred discipline.
3. Use the profile to adapt explanation depth, questions, routing, and output.
4. Preserve all existing stage boundaries and human gates.
5. Pass a compact context capsule to delegated agents instead of requiring each
   subagent to reread the full profile.

A context capsule should include only relevant information:

```text
Active user context:
- Preferred discipline: engineering
- Strong in reusable code and data design
- Needs support with 3D asset pipelines
- Human owns final design and visual selection
- Explain technical-art consequences for this task
```

Do not expose unrelated personal profile details to a delegated agent.

## Profile fields

Keep profiles small. `unknown` and `adaptive` are valid values and are preferred
to invented precision. Strength and guidance need are separate: a person may be
highly skilled while still wanting deep explanations in an unfamiliar area.

Ownership values describe collaboration preferences and additional review:

- `human`
- `agent_recommendation`
- `collaborative`
- `delegated_with_review`

Ownership settings may add human review requirements. They may not remove human
authority reserved by `human-interactions.md`, `decision-authority.md`, or the
relevant workflow.

## Missing or stale profiles

Do not block work because a profile is missing, incomplete, or stale. Use the
default profile and recommend `/review-profile` when useful.
