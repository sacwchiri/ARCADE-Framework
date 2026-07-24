# Project Agent Operating Rules

This project uses role-specific OpenCode agents under `.opencode/agents/`.

## Default workflow

1. Concept intake
2. Document selection
3. Pre-production planning
4. Blind spot review
5. Production slice planning
6. Human slice validation
7. Specialty implementation
8. Integration
9. Validation and playtesting
10. Ticket generation
11. Documentation curation

## Core human checkpoints

Humans must approve or answer:

- concept brief direction
- game pillars
- visual direction
- production slice strategy
- major technical tradeoffs
- prototype promotion to production
- interpretation of playtest results
- release readiness

## Review placement

Small reviews should be added directly inside the reviewed document under `Review Notes`.

Large cross-domain reviews should go under `/docs/reviews/`.

## Ticket command

Use `//ticket` to convert a bug, playtest observation, failed expectation, or issue into a structured ticket under `/docs/production/tickets/`.

## Agent safety

Planning agents should not edit source code.
Prototype code must be clearly labeled.
Implementation agents must read approved design and technical docs before editing.
Agents must separate decisions, assumptions, risks, open questions, and human decisions needed.
