---
name: bootstrap
description: Initialize a fresh Harness Designer clone by discovering the user's objective, current situation, important factors and immediate working needs, then creating only the minimum harness required to begin useful work.
---

# Bootstrap

Use this skill when `.harness/manifest.yaml` says `stage: bootstrap` or when the objective is materially undefined.

## Goal

Understand enough of the subject to start productive work without requiring the user to understand harness engineering first.

## Procedure

### 1. Discover before asking

Inspect the repository, existing files and currently available tools/connectors. Do not ask the user for information that can be established directly.

### 2. Ask a few high-information questions

Prefer roughly 3–5 adaptive questions over a fixed form. Choose the next question from what is still unclear.

Useful dimensions include:

- What are we ultimately trying to accomplish, and why now?
- What kinds of work, decisions or outputs will happen here?
- What would make the outcome excellent rather than merely acceptable?
- What sources, systems, people or tools influence the work?
- What constraints, boundaries or unacceptable failures matter?

Do not mechanically ask every dimension. If the user's first explanation already answers several, move forward.

### 3. Explore the problem, not just stated requirements

The user may not yet know all relevant factors. When useful, ask questions that reveal dependencies, actors, assumptions, failure modes, opportunities, relationships and missing information.

Avoid turning discovery into an endless interview. The objective can continue becoming clearer through real work.

### 4. Write the initial subject model

Update `.harness/objective.md` with what is actually known. Distinguish known constraints from open questions.

Update `.harness/manifest.yaml`:

- set a concise `subject`;
- set `objective_status` to `working` when enough is known to proceed;
- change `stage` from `bootstrap` to `active` once the first useful harness exists.

Create additional subject/context documents only when they already provide practical value.

### 5. Create the minimum viable harness

Use `skills/harness-designer/SKILL.md` to add only primitives clearly justified by the objective or immediate work.

Typical first-run output may be no more than:

- a clearer objective;
- one or two domain instructions;
- one useful skill;
- known tools/connectors;
- a small amount of state.

It is acceptable for the first harness to remain primitive.

### 6. Start real work

Do not end after configuration unless the user asked only for setup. Perform or advance the actual objective as soon as practical.

## Bootstrap success

Bootstrap is successful when a new session can answer:

1. What are we trying to accomplish?
2. What matters most right now?
3. What should I load or use for the current request?
4. What remains unknown?

It does not need a complete model of the subject.
