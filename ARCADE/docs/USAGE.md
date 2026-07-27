# Using the OpenCode Game Agent Workflow

This guide describes the smallest practical way to use the workflow, which agents are called at each stage, and what the human must do.

The workflow is intentionally not fully autonomous. Agents prepare decisions, plans, implementations, checks, and tickets. The human remains the creative owner, taste judge, playtester, and final approver.

## 1. Interaction model

OpenCode can invoke project subagents by `@` mention. This pack provides a primary Studio Orchestrator under `.opencode/agents/` and project commands under `.opencode/commands/` so the human can enter workflows without remembering long prompts. The Markdown files under `.opencode/workflows/` are source-of-truth process documents; they are read by the orchestrator and are not slash commands by themselves.

Use the **Studio Orchestrator** as the main agent. It selects only the specialists needed for the current work and stops at human decision gates. At each gate, specialists document their questions, but the orchestrator also presents every unresolved question directly through OpenCode's questionnaire UI and waits for the answer. Start OpenCode from the consuming project root. The repository `opencode.json` sets the orchestrator as the default primary agent, or it can be selected by cycling primary agents in the TUI. The commands below also target it directly.

Common entry points:

```text
/workflow-status
/concept <idea>
/preproduction <focus or constraints>
/plan-slices <project, system, or feature>
/execute-slice <approved slice name or number>
/integrate-slice <slice name or number>
/validate-slice <slice name or number>
/ticket <bug or playtest observation>
/curate <documentation area or change>
/art-pipeline <asset request>
/tool <approved tool capability request>
```

A specialist can also be called directly:

```text
@technical-architect compare a turn-based API with realtime networking for this match flow
@art-director define a placeholder visual target for the first playable slice
@blind-spot-reviewer review the current slice plan for underestimated work
@tool-controller generate concept-art candidates for the approved character brief
```

Specialists are subagents, not primary agents. They are expected to be called
with `@agent-name` or delegated to by the Studio Orchestrator.

After changing `opencode.json`, an agent, or a command, quit and restart
OpenCode so the new configuration is loaded.

Direct calls are useful for focused questions. Commands are preferred when moving work through a workflow stage.

## 2. The smallest complete example

Assume the project idea is:

> In Unity, the player presses a button, a single 3D die rolls, and the result from 1 to 6 is displayed.

This example is deliberately small. It still includes design, technical, UX, placeholder art, integration, validation, and human judgment.

### Stage 0 — Check current state

Human action:

```text
/workflow-status
```

The Studio Orchestrator reports whether the repository has an approved concept, a pending slice decision, implementation in progress, or validation waiting for human input.

For a new repository, the expected answer is: start with Concept.

---

### Stage 1 — Concept

Human action:

```text
/concept A small Unity proof where the player presses Roll, one 3D die rolls, and the final value from 1 to 6 is displayed. Single player, desktop, placeholder visuals, no networking or progression.
```

Agents normally involved:

- Director: clarifies purpose and scope.
- Systems Designer: defines the minimum roll behavior.
- UX Designer: defines button/result feedback.
- Technical Architect: identifies the simplest technical shape.
- Blind Spot Reviewer: checks for hidden scope or ambiguity.
- Documentation Curator: updates folder READMEs.

Expected outputs:

- `/docs/concept/concept-brief.md`
- `/docs/product/game-pillars.md` or a lightweight equivalent if needed
- `/docs/product/scope-boundaries.md`
- `/docs/product/open-questions.md`

Human action at the gate:

The Studio Orchestrator presents these questions directly in OpenCode. The
same decisions are also recorded in the concept documents:

- Is this a throwaway workflow prototype or production-intent code?
- Must the visual die physically land on the selected result, or is any animation acceptable?
- Is mouse input enough for the first version?
- Is the proposed scope correct?
- Should the idea proceed to pre-production?

The questionnaire uses explicit approval and modification choices. If changes
are requested, the orchestrator routes them back to the relevant agents and
asks the questionnaire again after the documents are updated.

The human does not need to edit every document manually. They approve, reject,
or correct decisions through the questionnaire, and the agents record those
answers in the documents.

---

### Stage 2 — Pre-production

Human action:

```text
/preproduction Focus on proving the OpenCode-to-Unity workflow. Use placeholders and avoid unnecessary architecture.
```

Agents normally involved:

- Systems Designer: makes the roll rules explicit.
- Technical Architect: defines result ownership and Unity structure.
- UX Designer: defines interaction and feedback states.
- Art Director or Technical Art: defines acceptable placeholder assets and import constraints.
- Validation: defines what must be demonstrated.
- Production Planner: identifies the smallest useful implementation path.
- Blind Spot Reviewer: checks whether the plan is still larger than the proof requires.

Expected outputs may include:

- a short prototype plan
- a minimal technical design
- a minimal interaction flow
- placeholder asset requirements
- a validation/playtest checklist

Human action at the gate:

Choose or approve:

- the main risk to prove first
- prototype versus production quality
- acceptable placeholder quality
- any major technical tradeoff
- whether the work is ready for slice planning

For this example, a reasonable human decision is:

> Treat it as a throwaway workflow prototype. The final number is authoritative; the die animation only needs to end on that face. Use one placeholder die, one button, and one result label.

---

### Stage 3 — Production slice planning

Human action:

```text
/plan-slices The Unity dice-roll proof of concept
```

The Production Planner proposes playable slices before detailed tasks.

A minimal proposal may be:

#### Slice 1 — Complete local dice-roll proof

Player-visible result:

- Open the Unity scene.
- Press Roll.
- See the die animate.
- See the value from 1 to 6.
- Press Roll again.

Minimum experience layers:

- Design: roll rules and allowed states.
- Gameplay: result generation and roll state.
- UX/UI: Roll button, disabled state while rolling, result feedback.
- Art: placeholder die and table/background.
- Audio/VFX: optional placeholders or explicitly excluded.
- Content: one die definition if data-driven content is needed.
- Integration: button → roll request → animation → result display.
- Validation: sanity checklist and human playtest.
- Documentation: implementation and setup notes.

Human action at the gate:

Answer:

- Is one slice enough?
- Should animation and result display be separated into two slices?
- Is any technical risk important enough to move earlier?
- Is this the correct first playable target?

For the smallest example, the human can reply directly in the same session:

```text
Approve one slice as proposed. Keep audio and VFX explicitly out of scope.
```

The agent then records the approval and finalizes milestones, tasks, dependencies, specialist assignments, and definition of done.

---

### Stage 4 — Production execution

Human action:

```text
/execute-slice Slice 1
```

The Studio Orchestrator checks that the slice is approved and delegates only the needed work.

Likely specialists:

- Gameplay Implementation: roll state and result logic.
- Unity Client Implementation: Unity scene/component integration.
- UI Implementation: Roll button and result label.
- Art Integration or Technical Art: placeholder die setup and import/prefab rules.
- Validation: prepares checks.
- Documentation Curator: updates setup and document indexes.

What the human does:

- Approves requested file edits or commands according to OpenCode permissions.
- Answers only when implementation would change approved behavior, scope, or quality.
- Does not micromanage ordinary coding choices already covered by the documents.
- Opens Unity for manual editor steps when an agent cannot safely complete them through available tools or MCP integrations.

The human should expect implementation handoffs that state files changed, checks run, manual Unity setup, assumptions, and risks.

---

### Stage 5 — Integration

Human action:

```text
/integrate-slice Slice 1
```

The Integration Agent checks the entire path:

```text
button click
→ roll request
→ generated result
→ die animation
→ roll completion
→ result label
→ button enabled again
```

What the human does:

- Resolves taste or ownership conflicts exposed by integration.
- Performs manual Unity wiring if required and not safely automated.
- Confirms the integrated scene can be opened and run.

Technical mismatches become tickets rather than being hidden inside handoffs.

---

### Stage 6 — Validation and human playtest

Human action:

```text
/validate-slice Slice 1
```

Agents perform or propose tool-checkable checks, then provide a short human playtest script.

Example human playtest:

1. Enter Play Mode.
2. Press Roll ten times.
3. Confirm every visible result is between 1 and 6.
4. Confirm the button cannot trigger overlapping rolls.
5. Confirm the displayed number matches the die face.
6. Confirm a second roll works without resetting the scene.
7. Note whether the interaction is clear and responsive.

What the human reports:

- What was clear?
- What was confusing?
- What felt slow or wrong?
- What broke?
- What did you expect instead?
- Accept, iterate, split, or reject the slice?

The human owns the final experience judgment.

---

### Stage 7 — Ticket generation

Suppose the result label changes before the die stops.

Human action:

```text
/ticket In build dice-poc-0.1, the result label appears immediately after pressing Roll, before the die finishes. Expected the result to appear when the die lands. Reproduces every roll in the Main scene.
```

The Validation Agent creates a structured ticket under:

```text
/docs/production/tickets/
```

The ticket includes the source build, expected and actual behavior, reproduction steps, area, owner recommendation, and acceptance criteria.

The human adds screenshots, video, or logs when they improve reproduction.

---

### Stage 8 — Documentation curation

Human action:

```text
/curate Slice 1 dice-roll implementation and validation
```

The Documentation Curator updates folder README inventories, cross-links, status, supersession notes, and contradictions.

The human normally only reviews the proposed documentation changes. The curator must not invent or reinterpret decisions.

## 3. Human responsibilities by stage

| Stage | Agent responsibility | Human responsibility |
|---|---|---|
| Concept | Structure the idea, identify scope and questions | Approve direction, pillars, and boundaries |
| Pre-production | Identify risks, prototypes, pipelines, and required docs | Choose risks, tradeoffs, visual target, and readiness |
| Slice planning | Propose playable slices, dependencies, and validation | Approve slice count, order, and first playable target |
| Execution | Delegate specialist work and produce handoffs | Approve permissions and resolve behavior/scope changes |
| Integration | Connect parallel work and expose mismatches | Resolve taste, ownership, or intended-behavior conflicts |
| Validation | Run sanity checks and prepare playtests | Play the build and judge fun, feel, clarity, and acceptance |
| Ticketing | Convert findings into actionable work | Supply impact, evidence, and reproduction context |
| Curation | Keep documentation coherent | Confirm that records reflect actual decisions |

## 4. Human interaction rules

The human should be asked only when the answer changes direction, cost, risk, scope, taste, or acceptance.

Agents should ask concrete questions such as:

- Should multiplayer be proven before the local core loop?
- Is this prototype allowed to be throwaway code?
- Is one slice enough, or should networking be isolated?
- Does this visual direction match the intended fantasy?
- Did the playtest result justify iteration or acceptance?

Agents should not interrupt the human for routine implementation details already governed by approved documentation.

When the human does not know the answer, they may respond:

```text
Recommend a default, explain the tradeoff, and mark it as an assumption pending validation.
```

## 5. When to call agents directly

Use a direct `@agent` call when the question belongs to one discipline and does not need a full workflow transition.

Examples:

```text
@systems-designer define the legal states for rerolling
@technical-art review this imported character asset for runtime constraints
@ux-designer review the accusation flow for comprehension problems
@content-designer estimate the minimum card set for the first playable match
@blind-spot-reviewer review the networking plan without changing the game premise
```

Use a slash command when the result should move the project from one stage to another and update project documentation.

## 6. Do not invoke every agent

The Studio Orchestrator should choose the minimum relevant team.

A tiny local dice prototype does not need backend, narrative, live operations, level design, or a full content pipeline.

A networked RTS may need systems design, technical architecture, UX, content design, level design, backend, simulation, technical art, integration, validation, and build/deployment support.

The genre and current slice determine the team.

## 7. Recommended daily loop

At the start of a work session:

```text
/workflow-status
```

Then perform one stage-sized action:

```text
/execute-slice Slice 1
```

or:

```text
/validate-slice Slice 1
```

At the end of meaningful work:

```text
/curate today’s Slice 1 work
```

Keep sessions centered on one workflow goal. Use tickets for findings that should not be fixed immediately.
