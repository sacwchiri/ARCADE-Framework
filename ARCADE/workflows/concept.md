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
- Tool Controller Agent, if a visual direction needs concept-image generation
- UX Designer Agent, if player flow or comprehension matters
- Content Designer Agent, if content scale matters
- Technical Architect Agent, if feasibility matters
- Blind Spot Reviewer Agent
- Documentation Curator Agent

## Required human interactions

Return these decisions to the active Concept stage agent. It must ask
them directly through OpenCode's `question` tool and record the answers in the
source-of-truth documents:

- concept direction
- game pillars
- visual direction, after reviewing a basic visual candidate when visual identity matters
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
- a basic concept-art candidate set and provenance handoff when visual identity matters

## Visual direction check

Written descriptors are not sufficient evidence for approving visual direction.
When visual identity, camera, composition, shape language, color, or mood matters:

1. The Art Director creates a compact visual brief with concrete scene content,
   camera/view, shape language, color language, lighting, mood, and explicit
   anti-references. Treat this as a hypothesis, not an approved style.
2. The Concept stage agent classifies the request as requiring image generation
   and runs the capability-verification protocol before delegating generation.
3. The Tool Controller produces the smallest useful candidate set, normally one
   to three images or equivalent quick studies. Do not generate a large set or
   final production art at this stage.
4. The candidate artifacts, prompts or source brief, provider, provenance, and
   validation status are recorded with the concept documents. Generated means
   candidate only; it does not mean approved or production-ready.
5. The Concept stage agent asks the human to review the candidates directly and
   records one of `Approved`, `Approved with changes`, `Rejected`, or
   `Not applicable`. If changes are requested, revise the brief and repeat the
   check before treating visual direction as approved.

If image generation is unavailable, the workflow must pause for the explicit
capability decision described in the capability-verification protocol. A human
may choose to defer, skip with a documented reason, or stop; the workflow must
not present an untested written style as an approved visual direction.

## Exit criteria

- The concept can be explained in one paragraph.
- Major pillars are clear.
- Scope boundaries are clear enough for pre-production.
- Open questions are listed.
- Human decision points are explicit.
- If visual identity matters, the human has reviewed basic visual evidence and
  the accepted direction is recorded with its candidate provenance.
