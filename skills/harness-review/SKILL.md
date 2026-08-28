---
name: harness-review
description: Review an evolved harness for duplication, stale assumptions, unnecessary complexity and misplaced primitives; consolidate or retire components while preserving useful capability.
---

# Harness Review

Use periodically, after substantial growth, after a model/tool change, or when the harness feels harder to understand than the work itself.

## Review questions

For each active component:

1. What current problem does this solve?
2. Is that problem still present?
3. Is the component actually being used?
4. Does another component now cover the same need?
5. Is this the correct primitive?
6. Could it be shorter or loaded only when relevant?
7. Does it encode an assumption about an older model, tool or workflow that no longer holds?
8. What would break if it were removed?

## Actions

Choose one:

- **keep** — still useful and appropriately placed;
- **simplify** — same value with less context/maintenance;
- **merge** — consolidate overlapping components;
- **move** — place the content in a more suitable primitive;
- **revise** — retain the primitive but update its procedure/assumptions;
- **retire** — remove from active use while keeping rationale/history when useful.

## Review priorities

Check these first:

- large entry instructions;
- skills with overlapping triggers;
- hooks that duplicate model behavior;
- repeated context loaded on every session;
- stale tool/authentication procedures;
- contradictory instructions;
- loops without clear stopping conditions or useful verification;
- evaluations that reward proxy behavior rather than the real objective.

## Outcome

The goal is not a larger or more sophisticated harness. The goal is the **least structure that reliably supports excellent work for the current objective**.

Update `.harness/manifest.yaml` and relevant evolution notes after material changes.
