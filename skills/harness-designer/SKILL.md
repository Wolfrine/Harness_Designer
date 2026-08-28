---
name: harness-designer
description: Decide when a discovery from real work deserves persistent harness structure, choose the smallest appropriate primitive, and implement the change without creating unnecessary scaffolding.
---

# Harness Designer

Use this skill when real work reveals a durable pattern, repeated friction, missing capability, important invariant or reusable procedure.

## First question

**Will persisting this materially improve future work?**

If not, leave it in the conversation.

## Classification

| Pattern | Prefer |
|---|---|
| Stable fact/reference | Knowledge/docs |
| Broad behavioral rule | Instruction |
| Reusable procedure with judgment | Skill |
| Deterministic lifecycle/guard behavior | Hook |
| Quality criterion that can be checked | Evaluation |
| External access/capability | Tool/connector |
| Distinct specialist perspective/context | Agent |
| Repeated process with recurrence/state | Loop |
| Mutable current position | State |
| Important historical choice | Decision record |

When two primitives could work, choose the simpler one unless the stronger mechanism solves a real failure mode.

## Design test

Before adding something, check:

1. **Evidence** — What happened that justifies it?
2. **Recurrence** — Is this likely to matter again?
3. **Existing coverage** — Is there already a rule, skill or tool that should be improved instead?
4. **Placement** — Is this information, procedure, enforcement, evaluation or state?
5. **Cost** — What context, maintenance or rigidity does it add?
6. **Validation** — How would we know the change helped?
7. **Removal** — Under what condition should it be consolidated or retired?

## Candidate-first behavior

Prefer a candidate change before canonical promotion when:

- the pattern has been seen only once;
- the abstraction is uncertain;
- the proposed automation could create side effects;
- the change materially constrains future agent behavior.

Immediate promotion is reasonable for an explicit durable user instruction, an obvious missing procedure repeatedly needed, or a high-consequence invariant.

## Implementation guidance

### Instructions

Keep invariant guidance concise. Do not turn `AGENTS.md` into a knowledge base.

### Skills

A skill should have a clear trigger, outcome, procedure and validation method. Store references/scripts beside it only when they are actually needed.

### Hooks

Use hooks for deterministic lifecycle behavior or guards. State the event, behavior, inputs/outputs, failure behavior and idempotency expectations. Prefer portable contracts first; create runtime-specific adapters only when justified.

### Evaluations

Define what is being judged and what evidence counts. Prefer observable criteria over vague self-assessment.

### Tools/connectors

Document what capability the tool adds, authentication assumptions, failure modes and any maintenance workflow that repeatedly matters.

### Agents

Create specialist agents only when separate context, permissions, expertise or parallel reasoning creates meaningful value.

### Loops

Specify trigger, state, stopping condition, verifier and escalation behavior. Avoid endless autonomous cycles without a clear oracle or budget.

## After implementation

- Update `.harness/manifest.yaml` if the active structure changed.
- Keep detailed rationale in `.harness/evolution/` when the decision is non-obvious or likely to need later review.
- Do not add multiple overlapping primitives for the same problem.
