---
name: core-principles
description: Use a project's core principles file as a decision gate. Use when a repo has CORE_PRINCIPLES.md, PRINCIPLES.md, a seed/product principles file, or an equivalent project constitution, and Codex is planning, implementing, reviewing, or discussing changes that may affect product direction, architecture, UX, data ownership, security boundaries, workflow, scope, or non-goals.
---

# Core Principles

Use this skill to preserve a project's load-bearing rules instead of treating
implementation tasks as isolated code changes.

## Find The Principles

Before non-trivial work, look for the project's principles source in this order:

1. Explicit file named by the user or repo instructions.
2. `CORE_PRINCIPLES.md`.
3. `PRINCIPLES.md`.
4. Product seed, project memory, or architecture docs that the repo names as
   source of truth, such as `lens-seed.md`, `product.md`, or `.codex/project.md`.

If multiple files disagree, follow the repo's stated source-of-truth order. If
there is no stated order, prefer the most explicit principles file and mention
the ambiguity when it matters.

## Workflow

1. Read the relevant principles file before deciding an approach.
2. Identify which principles the task touches.
3. Treat those principles as constraints, not background flavor.
4. Shape the implementation, review, or recommendation so it strengthens the
   principles where possible.
5. If a request conflicts with a principle, pause the happy path and state the
   conflict plainly. Either reshape the change or ask for/record a deliberate
   exception.
6. When editing derived docs or skills, update the source-of-truth file first,
   then propagate the change to summaries or mirrors.

## Review Gate

For meaningful product, architecture, UX, data, security, workflow, or scope
changes, include a short mental checklist:

- Which principle(s) does this touch?
- Does the change make the principle easier or harder to uphold later?
- Is the change adding a second system, exception, or hidden state?
- Is the user-facing behavior consistent with the intended audience?
- Is any exception explicit, documented, and intentionally narrow?

## Output Style

Be concise. Usually mention only the principle numbers or names that matter.
Do not paste the whole principles file back to the user unless they ask.

For code work, implement the aligned approach after applying the gate. For
reviews, lead with violations or drift risks before general observations.
