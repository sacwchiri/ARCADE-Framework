# Workflow: Concept

Use this workflow when a raw idea, feature idea, system idea, visual direction, technical question, or external inspiration needs to become a clear concept.

## Goal

Answer:

- What is this?
- Why does it matter?
- What needs to exist?
- What is out of scope?
- What should happen next?

## Default agents

- Director Agent
- Systems Designer Agent
- Art Director Agent, if visual identity matters
- UX Designer Agent, if player flow or comprehension matters
- Content Designer Agent, if content scale matters
- Technical Architect Agent, if feasibility matters
- Blind Spot Reviewer Agent
- Documentation Curator Agent

## Required human interactions

Return these decisions to the Studio Orchestrator. The orchestrator must ask
them directly through OpenCode's `question` tool and record the answers in the
source-of-truth documents:

- concept direction
- game pillars
- visual direction
- scope boundaries
- whether the concept should proceed to pre-production

## Outputs

- Create `docs/` and the required domain folders and `README.md` indexes before
  writing the first project documents; create only the domains selected for this
  concept.
- `/docs/concept/concept-brief.md`
- `/docs/product/game-pillars.md`
- `/docs/product/scope-boundaries.md`
- `/docs/product/open-questions.md`
- folder README updates

## Exit criteria

- The concept can be explained in one paragraph.
- Major pillars are clear.
- Scope boundaries are clear enough for pre-production.
- Open questions are listed.
- Human decision points are explicit.
