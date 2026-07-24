# Protocol: Document Selection

Agents should let the project define its documents. Do not force every game into the same document set.

## Steps

1. Classify scale:
   - Project
   - System
   - Feature
   - Task
   - Bug
   - Research

2. Classify domains:
   - Concept
   - Product
   - Design
   - Technical
   - Art
   - UX
   - Content
   - Audio
   - Narrative
   - Levels
   - Production
   - Validation
   - Release
   - LiveOps

3. Identify genre implications:
   - Cards
   - Puzzle
   - Shooter
   - RTS
   - RPG
   - Simulation
   - Strategy
   - Platformer
   - Multiplayer
   - LiveOps
   - Procedural
   - Narrative-heavy

4. Decide current documents needed.

5. Bootstrap only the documentation paths required by the current workflow:
   - create `docs/` when the first project document is needed;
   - create each required domain folder on demand;
   - create the domain `README.md` before or alongside the first document in
     that folder;
   - create `docs/README.md` when project-level navigation or multiple domains
     make a root index useful.

6. Update the relevant folder README with new, renamed, obsolete, or re-scoped documents.

## Bootstrap Rule

The workflow pack does not provide a pre-seeded project `docs/` directory. A
workflow or subagent that creates project documentation is responsible for
creating the required folders and README indexes as part of that work. Do not
fail because an expected documentation folder or README is missing.

## Rule

No document without:

- a reader
- an owner
- a decision or workflow it supports
