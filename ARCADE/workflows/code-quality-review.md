# Evaluate Activity: Code Quality Review

Use this activity when implementation quality, maintainability, compatibility,
or test organization needs an evidence-based review.

## Goal

Find defects and maintainability risks before they become architectural or
production debt. Reviewers recommend changes; they do not silently fix the work.

## Default agents

- Code Quality Reviewer Agent
- Technical Architect Agent, when boundaries or compatibility are involved
- Validation Agent, when missing regression coverage is involved
- Documentation Curator Agent, when the review changes documented conventions

## Review checks

- Clear domain names and no misleading generic type names.
- Braced control-flow bodies; no compressed statements that reduce readability.
- Focused files and folders with one coherent responsibility.
- Composition over inheritance and no speculative abstraction layers.
- Comments for invariants, compatibility workarounds, deterministic ordering,
  persistence field order, or measured performance decisions.
- No Unity dependencies in portable simulation/application code.
- No unsupported C# or BCL APIs for the pinned Unity profile.
- Public API, serialization, AOT, and migration compatibility.
- Tests grouped by behavior with reusable fixtures and meaningful assertions.
- No stale generated artifacts, unrelated edits, or hidden scope expansion.

## Required output

Findings come first and are ordered by severity. Every finding includes a file
and line reference, impact, evidence, and a recommended change. Separate
confirmed findings from assumptions and checks that could not run.

## Human interaction

The reviewer does not require a human decision for ordinary maintainability
findings. Ask the human when the proposed fix changes public behavior,
architecture, scope, quality targets, or final taste.
