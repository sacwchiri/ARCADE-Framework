# Protocol: Handoff

Every agent handoff should make the next step obvious.

## Handoff template

```markdown
# Handoff: [Work Item]

## Completed
- 

## Source of Truth Used
- 

## Files Changed
- 

## Decisions Made
- 

## Assumptions
- 

## Deviations
- 

## Risks
- 

## Needs From Other Agents
- 

## Human Decisions Needed
- Status: Pending / Approved / Approved with changes / Rejected / Not applicable
- Question:
- Context:
- Options or recommendation:
- Answer or requested changes:

## Recommended Next Step
- 
```

The `Human Decisions Needed` section is an input to the active stage agent's
direct questionnaire. A handoff must not leave a required decision only in this
section: the stage agent presents it through OpenCode's `question` tool, waits
for the answer, and records the result in the relevant source-of-truth document.

## Common handoff paths

- Director → Systems Designer
- Systems Designer → Technical Architect
- Technical Architect → Production Planner
- Production Planner → Specialty Implementation Agents
- Implementation Agents → Integration Agent
- Integration Agent → Validation Agent
- Validation Agent → Ticket Generation
- Any Agent → Documentation Curator
