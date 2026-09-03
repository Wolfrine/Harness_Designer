---
name: bootstrap
description: Discover the subject objective, current situation, important factors and immediate working needs after repository identity is safely established, then create only the minimum harness required to begin useful work.
---

# Bootstrap

Use this skill when `.harness/manifest.yaml` says `stage: bootstrap` or when the objective is materially undefined.

Repository identity must already be established. If the subject repository is not yet clearly the sole project repository, use `skills/repository-initializer/SKILL.md` first.

## Goal

Understand enough of the subject to start productive work without requiring the user to understand harness engineering first.

It is valid to know the subject name while leaving the objective in bootstrap until the user provides enough context.

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

### 3. Offer the Harness Dashboard once

During initial bootstrap, resolve the dashboard preference explicitly unless it is already recorded in `.harness/manifest.yaml`.

Ask the user a concise question such as:

> Would you like a local Harness Dashboard that shows what agent sessions have happened, what remains open, and how the harness is evolving over time?

Make clear that:

- it is optional;
- it is local by default;
- it can be enabled later;
- if enabled, the LLM generates a dashboard suited to this subject from Harness Designer's basic structure rather than installing a rigid universal UI.

If the user says **yes**:

- set `observability.dashboard: enabled`;
- use `skills/harness-dashboard/SKILL.md` after the initial subject model is sufficiently understood;
- enable repository-local trajectory persistence only to the extent needed by the subject/runtime, or adapt an existing durable runtime trajectory source.

If the user says **no**:

- set `observability.dashboard: disabled`;
- leave `dashboard_path: null`;
- do not ask again on later sessions unless the user reopens the choice.

Dashboard preference is a product/observability choice, not a request for the user to design harness primitives.

### 4. Explore the problem, not just stated requirements

The user may not yet know all relevant factors. When useful, ask questions that reveal dependencies, actors, assumptions, failure modes, opportunities, relationships and missing information.

Avoid turning discovery into an endless interview. The objective can continue becoming clearer through real work.

### 5. Write the initial subject model

Update `.harness/objective.md` with what is actually known. Distinguish known constraints from open questions.

Update `.harness/manifest.yaml`:

- set a concise `subject` when known;
- keep `objective_status` in bootstrap/uninitialized while material objective context is still missing;
- set `objective_status` to `working` when enough is known to proceed;
- change `stage` from `bootstrap` to `active` once the first useful subject-specific harness exists;
- preserve the resolved dashboard preference.

Do not invent objective details merely to complete initialization.

Create additional subject/context documents only when they already provide practical value.

### 6. Create the minimum viable harness

Use `skills/harness-designer/SKILL.md` to add only primitives clearly justified by the objective or immediate work.

Typical first-run output may be no more than:

- a clearer objective;
- one or two domain instructions;
- one useful skill;
- known tools/connectors;
- a small amount of state;
- an optional generated Harness Dashboard if the user opted in.

It is acceptable for the first harness to remain primitive.

If the dashboard is enabled, use `skills/harness-dashboard/SKILL.md` to create it from the subject context and the template contract. Do not delay useful subject work to perfect the dashboard.

### 7. Start real work

Do not end after configuration unless the user asked only for setup. Perform or advance the actual objective as soon as practical.

## Bootstrap success

Bootstrap is successful when a new session can answer:

1. What are we trying to accomplish?
2. What matters most right now?
3. What should I load or use for the current request?
4. What remains unknown?
5. Is the optional Harness Dashboard enabled, disabled or intentionally still undecided?

It does not need a complete model of the subject.
