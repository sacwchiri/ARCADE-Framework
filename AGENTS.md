# Repository Instructions

This repository is an OpenCode workflow/documentation pack, not the game project that consumes it. Role definitions live in `.opencode/agents/`; workflows and protocols there are the source of truth for process details.

## Workflow

Use the smallest relevant path: concept -> pre-production -> slice planning -> approved execution -> integration -> validation/playtest -> ticketing -> documentation curation. Do not skip approval gates when direction, scope, architecture, visual target, or acceptance is changing.

## Human authority

Humans own core fantasy, pillars, audience/platform, scope changes, visual and feel quality, slice plan, playtest interpretation, prototype promotion, and release readiness. Agents may recommend and implement approved decisions, but must ask concrete questions rather than silently changing them.

## Editing rules

- Planning agents do not edit implementation code; prototype code must be explicitly labeled.
- Implementation agents must read the approved task and relevant design/technical docs, inspect existing content, edit only approved scope, and run available checks.
- If behavior, architecture, visual direction, or scope must change, stop and escalate before editing beyond the approved task.
- Every handoff should identify source-of-truth docs, changed files, decisions, assumptions, deviations, risks, human decisions, and the next step; use `.opencode/protocols/handoff.md`.
- Create only documents with a reader, owner, and supported decision/workflow; update the relevant `docs/*/README.md` index when documents are added, renamed, or obsolete.

## Reviews and tickets

Put small reviews under `Review Notes` in the reviewed document; put cross-domain reviews in `docs/reviews/`. Use the ticket workflow (`//ticket`) for bugs, playtest observations, failed expectations, or other issues; tickets belong in `docs/production/tickets/`.

## Tooling

There is no root build, test, lint, or typecheck command. The only package manifest is `.opencode/package.json`, which declares the OpenCode plugin dependency; do not invent application commands for this repository.
