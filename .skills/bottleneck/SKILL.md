---
name: bottleneck
description: Interview the user to identify the single highest-leverage issue preventing meaningful progress toward a project's goal, before choosing work. Use only when explicitly invoked as `$bottleneck` for a top-level strategic reset, next-step planning, feature-prioritization, release readiness, growth, onboarding, validation, or when deciding whether data collection is more valuable than building. Do not conclude or write `BOTTLENECK.md` until the interview has established the goal, reality, and competing interventions; then present and record the diagnosis without implementing or delegating the resulting work.
---

# Bottleneck

Use this skill to interrupt feature momentum and name the one issue whose improvement is most likely to advance the current goal. A bottleneck may be external or non-technical: demand, reach, activation, retention, release readiness, a decision, knowledge, or a workflow.

## Operating stance

- Treat a single bottleneck as the best current diagnosis, not an excuse for false certainty or endless analysis.
- State evidence separately from inference. When data is sparse, make a reasonable hypothesis but say exactly why it is provisional and what observation would change it.
- Optimize for goal-level movement and end-to-end user value, never activity, code volume, feature count, or local convenience.
- Apply subtraction before construction: challenge the requirement and delete or defer non-lever work before optimizing, accelerating, automating, or adding scope.
- Keep the analysis brief. The artifact serves a decision; it must not become a planning system.

## Workflow

### 1. Interview before diagnosis

Inspect the repository and any existing `BOTTLENECK.md`, product notes, analytics, release state, user feedback, and prior decisions to make the interview specific. Do not present a bottleneck, recommend work, or change `BOTTLENECK.md` during this inspection.

Run a real, collaborative interview. Ask one decisive question at a time and wait for the answer; do not send a questionnaire or hide a conclusion inside a question. In the normal case, ask at least three questions, tailored to what is learned. Establish:

- The outcome the user actually wants now and why it matters.
- What is known about the path to that outcome: users, release state, behaviour, feedback, or operational reality.
- The competing moves the user is tempted to make, and the assumptions behind them.

Ask further questions when the answer could materially change the selected lever. A useful sequence often moves from outcome → observed reality → candidate interventions, but never follow a script at the expense of a decisive question. If the user explicitly requests a quick pass, declines questions, or lacks the information, proceed only after making that limitation explicit in the eventual record.

Phrase the goal as a concrete outcome, not an output. Examples: “new visitors complete onboarding,” “the product is ready for its first real release,” or “existing users return to use the core workflow.” Do not invent a new goal merely to fill a template.

### 2. Diagnose the value path

Map only the smallest relevant path from input to goal outcome. For a product, this may be acquisition → activation → repeated value; for a release, it may be release blocker → usable deployment → user feedback.

Use the available evidence to identify where value is actually limited. Look for such signals as:

- A step with negligible reach or completion relative to the preceding step.
- A missing release, distribution channel, measurement path, or user feedback loop.
- Repeated rework, waiting, handoffs, or a decision that blocks all downstream work.
- A proposed feature that does not address the goal's limiting step.

If the evidence cannot identify a constraint confidently, choose the smallest useful learning move or state the strongest reasonable hypothesis. Do not pretend that unmeasured feature ideas are validated.

### 3. Rank candidates and choose one

Consider a short list of plausible constraints. For each, use the counterfactual: “If this materially improved now, would the goal move more than if the alternatives improved?”

Select exactly one current bottleneck. Name:

- The evidence and reasoning.
- The non-feature alternative, if applicable (for example: measure, speak to users, ship, market, simplify, or remove a requirement).
- The smallest next action that directly tests or relieves it.
- What would disconfirm the diagnosis.

Do not choose a feature merely because it is easy to make. Do not create a roadmap, backlog, review cadence, target metric, or routine unless the user explicitly asks for one.

### 4. Present, then record

Only after the interview, present a concise diagnosis before changing files. Include the goal, the bottleneck, supporting evidence versus assumptions, why feature work is or is not the lever, and the recommended next action. Unless the user rejects or redirects the diagnosis, update the record immediately afterward; do not require a separate approval to preserve it.

Create or update `BOTTLENECK.md` at the repository root. Preserve the single current entry and a minimal history. If the file already exists, retain useful context and move replaced entries to history rather than rewriting it wholesale.

Use this shape, adapting only when existing repository convention makes a better concise form obvious:

```markdown
# Bottleneck

## Current

### Goal
<the current outcome>

### Bottleneck
<the one highest-leverage issue>

### Why this is the lever
- Evidence: <observations/data>
- Inference: <reasoning and confidence, if needed>
- Would change my mind: <specific observation>

### Next action
<one smallest action that tests or relieves the bottleneck>

### Explicitly not now
<parked work that does not address this bottleneck>

## History

- <previous goal/bottleneck — outcome or why it was superseded, if known>
```

Do not manufacture a history. Append only material prior goals or superseded bottlenecks so future sessions can assess whether the lever helped or the goal changed.

### 5. Stop at strategy

Do not begin implementation, create a feature branch, execute the recommended work, or dispatch agents as part of this skill. The user explicitly initiates the next action, whether in the same task or a new one.
