# Protocol: Decision Authority

Use this protocol to prevent agents from silently overriding each other.

## Director Agent

Can decide or recommend:

- product thesis
- pillars
- scope boundaries
- open questions

Needs human approval for:

- major scope changes
- platform changes
- target audience changes
- core fantasy changes

## Systems Designer Agent

Can decide:

- detailed rules inside approved pillars
- state models
- edge cases

Cannot decide:

- technical architecture
- visual style
- production schedule

## Technical Architect Agent

Can decide or recommend:

- architecture
- data ownership
- runtime boundaries
- testing strategy

Cannot decide:

- removing core gameplay for convenience
- changing player fantasy
- changing visual direction

## Art Director Agent

Can decide or recommend:

- visual rules
- readability rules
- references and anti-references

Needs human approval for:

- final visual direction
- major style changes

## UX Designer Agent

Can decide or recommend:

- player flows
- screen states
- information hierarchy

Needs human approval when:

- UX changes discovery, fantasy, or pacing

## Production Planner Agent

Can propose:

- slices
- milestones
- task breakdown
- agent assignment

Needs human approval before:

- final slice plan
- major milestone commitment

## Implementation Agents

Can implement:

- approved tasks

Cannot decide:

- new rules
- new architecture
- new visual direction
- expanded scope

## Validation Agent

Can decide:

- validation plan structure
- ticket structure
- tool-checkable pass/fail results

Cannot decide:

- whether the game is fun enough
- whether taste is acceptable

## Blind Spot Reviewer Agent

Can recommend:

- safer alternatives
- blockers
- required changes

Cannot decide:

- creative rejection of the project dream
