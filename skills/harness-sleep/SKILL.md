---
name: harness-sleep
description: Run an offline consolidation cycle using a fresh agent perspective to review recent trajectories and outcomes, identify systemic patterns, improve the harness, prune unnecessary structure, and validate candidate changes before future work resumes.
---

# Harness Sleep

Use when accumulated work provides enough evidence that the harness itself may need consolidation or structural improvement.

Typical triggers include repeated weak outcomes, repeated user correction, recurring friction, meaningful harness growth, conflicting instructions or skills, a model/tool/runtime change, an unusually strong result worth understanding, or an explicit request to improve the harness from recent experience.

This is not a mandatory end-of-session ritual. Prefer meaningful evidence over fixed schedules.

## Principle

Separate **doing the work** from **improving the system that does the work**.

A sleep cycle should preferably be performed by a fresh agent/session that did not produce the recent trajectories being reviewed. The consolidator should independently reconstruct the objective and current harness before judging prior behavior.

The first question is not whether prior agents followed instructions. It is:

**Did the current harness cause agents to produce meaningful outcomes for the objective?**

## Inputs

Use evidence already available before creating new logging machinery:

- `.harness/trajectory/sessions/` when the subject has enabled repository-local trajectory evidence;
- durable runtime-native trajectories or conversations;
- user corrections and feedback;
- Git commits, diffs and issue history;
- evaluation results;
- candidate evolution notes;
- observable task outcomes;
- existing harness structure.

If an optional Harness Dashboard is enabled, treat its underlying trajectory/evolution evidence as input; do not reason from the rendered dashboard alone when canonical sources are available.

Create explicit experience logs only when the runtime otherwise cannot provide enough evidence for useful consolidation or the user has opted into observability that needs durable history.

## Sleep cycle

### 1. Reconstruct

- Read `.harness/manifest.yaml`, `.harness/objective.md` and `.harness/architecture.md`.
- Understand the subject repository and what successful work means.
- Inspect the active instructions, skills, hooks, evaluations, tools, agents, loops and state relevant to recent work.
- Inspect trajectory/evidence configuration and dashboard state when present.

Do this before interpreting prior trajectories so the consolidator has an independent model of the system.

### 2. Review outcomes

Inspect several recent trajectories when available, not only the latest one.

For each meaningful trajectory ask:

1. What was the intended outcome?
2. Was the result actually useful?
3. What worked unusually well?
4. What failed or required correction?
5. Was the cause task-specific, model-specific, tool-specific, context-specific, or harness-level?
6. Did the harness help, interfere, or remain irrelevant?
7. Did the session create harness evidence or modify harness components?

### 3. Abstract across trajectories

Look for cross-run patterns:

- recurring failure modes;
- repeated user corrections;
- duplicated reasoning or manual work;
- successful strategies that should become reusable;
- conflicting or stale instructions;
- missing capabilities;
- skills that should merge or split;
- procedures that can be simplified;
- special-case patches that reveal a broader invariant;
- components that no longer earn their context or maintenance cost;
- repeated open threads or forks that indicate unresolved systemic friction.

Do not convert every observation into a harness change.

### 4. Consolidate

Use `skills/harness-review/SKILL.md` to simplify, merge, move, revise or retire active components where justified.

Use `skills/harness-designer/SKILL.md` for genuinely new durable structure.

Prefer replacing several narrow patches with one better abstraction when evidence supports it.

### 5. Generate candidate mutations

For material changes, create isolated candidate changes before promotion when practical.

A candidate should state:

- evidence from trajectories/outcomes;
- the systemic problem or opportunity;
- proposed harness mutation;
- expected benefit;
- possible regressions;
- how it will be evaluated;
- retirement condition.

Where repository-local trajectory shards exist, reference the relevant session ids rather than duplicating entire histories into the candidate note.

### 6. Validate

Before making a material mutation canonical:

- compare against the current harness;
- replay representative prior tasks when practical;
- check that known successful behavior is preserved;
- check that the target failure or friction is reduced;
- reject changes that only move complexity elsewhere without improving outcomes.

Prefer observable evidence over self-assessed improvement.

### 7. Wake

Promote only changes that have sufficient evidence and acceptable regression risk.

Update `.harness/manifest.yaml` and relevant evolution notes after material consolidation.

If repository-local trajectory shards were reviewed, optionally add lightweight review metadata such as `sleep.reviewedAt` and `sleep.cycle` without rewriting or discarding the original evidence.

If the Harness Dashboard is enabled, regenerate or refresh it so the user can see the completed sleep cycle and resulting harness changes.

Future agents should then operate using the evolved harness without needing the full sleep analysis in their normal context.

## Isolation

Sleep is an offline harness-improvement mode.

While experimenting with candidate harness mutations, avoid unrelated real-world subject actions. If the runtime permits it, use isolated branches, sandboxes, shadow copies or equivalent candidate environments for risky changes.

The consolidator may reason, inspect, simulate and test extensively without granting candidate behavior unnecessary production authority.

## Online vs sleep evolution

Use **online evolution** for clear high-confidence discoveries during work: explicit durable user instructions, obvious missing procedures, repeated known needs, or high-consequence invariants.

Use **sleep evolution** when the useful signal emerges across multiple trajectories or requires reconsidering how several harness components work together.

## Outcome

The goal is not to make the harness larger after every sleep cycle.

A successful sleep cycle leaves future agents with a harness that is more coherent, more effective, and usually no more complex than necessary — while any enabled dashboard makes that evolution understandable to the user.
