# Workflow: Ticket Generation

Use this workflow when the user invokes `/ticket`, writes `//ticket`, or asks to convert an issue, bug, playtest note, failed expectation, or observation into actionable work.

## Owner

Validation Agent.

## Ticket location

`/docs/production/tickets/`

If the project has no `docs/` directory or ticket index yet, create `docs/`,
`docs/production/`, `docs/production/tickets/`, and the corresponding
`README.md` indexes before creating the first ticket.

## Ticket template

```markdown
# Ticket: [Short Title]

## Type
Bug / Design Issue / Technical Debt / UX Issue / Content Issue / Balance Issue / Performance Issue / Art Issue / Audio Issue / VFX Issue / Integration Issue

## Source
Human playtest / QA sanity check / Automated test / Blind spot review / Production review / Integration review

## Version / Build

## Severity
Critical / High / Medium / Low

## Priority
P0 / P1 / P2 / P3

## Area
Gameplay / Backend / UI / UX / Art / Audio / VFX / Content / Networking / Tools / Economy / Build / Integration

## Description

## Expected Result

## Actual Result

## Reproduction Steps
1.
2.
3.

## Evidence
Screenshots, logs, video, test output, save file, player notes.

## Suspected Cause
Optional. Include only if known.

## Suggested Owner

## Related Documents

## Acceptance Criteria
- [ ] Issue no longer reproduces.
- [ ] Related checklist/test updated.
- [ ] Documentation updated if behavior changed.
```

## Human interactions required

Return missing reproduction steps, build version, evidence, or impact to the
Studio Orchestrator. It must request the information directly through
OpenCode's `question` tool before finalizing the ticket when those details are
required. If the human does not know an item, record an explicit placeholder.
