# Harness Evolution

This directory holds the reasoning trail for meaningful harness changes when such a trail is useful.

## Lifecycle

```text
candidate → active → revised / retired
```

A candidate should normally answer:

- What repeated friction, opportunity or invariant was observed?
- What evidence supports changing the harness?
- Which primitive is proposed, and why is it the smallest adequate one?
- What existing component overlaps with it?
- How can usefulness be checked?
- What would cause the change to be removed later?

## Promotion guidance

Promote a candidate when at least one of these is true and the change has clear future value:

- the pattern has appeared repeatedly;
- the user explicitly establishes it as a durable rule or workflow;
- it protects a high-consequence correctness, security or operational invariant;
- an evaluation shows material improvement.

Do not require formal candidate files for trivial edits. The purpose is judgment and reversibility, not bureaucracy.

## Review

Periodically review active harness components for:

- duplication;
- contradictions;
- stale assumptions;
- procedures that newer models or tools no longer need;
- rules that belong in a different primitive;
- components that cost more context or maintenance than the value they provide.

Retirement is a normal part of learning.
