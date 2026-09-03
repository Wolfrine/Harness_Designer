# Harness Evolution

This directory holds the reasoning trail for meaningful harness changes when such a trail is useful.

Harness Designer evolves through two complementary paths:

- **online evolution** — a durable improvement becomes clear during active work;
- **sleep evolution** — a fresh consolidator reviews multiple trajectories and outcomes to improve the harness as a system.

## Lifecycle

```text
candidate → active → revised / retired
```

A candidate should normally answer:

- What repeated friction, opportunity or invariant was observed?
- What trajectory or outcome evidence supports changing the harness?
- Is the issue local to one task, or systemic across the harness?
- Which primitive is proposed, and why is it the smallest adequate one?
- What existing component overlaps with it?
- How can usefulness be checked against actual outcomes?
- What regressions are plausible?
- What would cause the change to be removed later?

When repository-local trajectory evidence exists, reference relevant session ids/shards instead of copying whole session histories into the evolution note.

## Promotion guidance

Promote a candidate when at least one of these is true and the change has clear future value:

- the pattern has appeared repeatedly;
- the user explicitly establishes it as a durable rule or workflow;
- it protects a high-consequence correctness, security or operational invariant;
- an evaluation shows material improvement;
- sleep review shows a consistent cross-trajectory pattern and the candidate improves outcomes without unacceptable regression.

Do not require formal candidate files for trivial edits. The purpose is judgment and reversibility, not bureaucracy.

## Sleep consolidation

When useful evidence has accumulated across agents or sessions, use `skills/harness-sleep/SKILL.md`.

The consolidator should preferably be a fresh agent/session. It should reconstruct the objective and current harness, review several recent trajectories, judge whether the resulting work was actually meaningful, then identify systemic improvements.

Sleep may consolidate, simplify, merge, revise or retire existing components as well as create new candidates. A successful sleep cycle may make the harness smaller.

Use existing runtime/conversation/Git/evaluation evidence before adding dedicated trajectory logs. When the user has opted into the Harness Dashboard, repository-local trajectory evidence may already exist and should be reused rather than duplicated.

## Dashboard visibility

If the Harness Dashboard is enabled, evolution records can be surfaced there so the user can see what changed and why. The dashboard remains a view over this directory, the manifest, trajectory evidence and Git history; it is not the canonical evolution record.

## Review

Periodically review active harness components for:

- duplication;
- contradictions;
- stale assumptions;
- procedures that newer models or tools no longer need;
- rules that belong in a different primitive;
- components that cost more context or maintenance than the value they provide;
- components that agents follow but that do not improve objective outcomes.

Retirement is a normal part of learning.
