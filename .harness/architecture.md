# Harness Architecture

Harness Designer separates subject understanding from harness structure. The user should be able to discuss the work naturally; the agent decides what, if anything, deserves persistent structure.

## Placement model

| Observation | Default destination |
|---|---|
| Stable domain fact or reference | Knowledge/docs |
| Stable behavioral principle | Instruction |
| Repeatable procedure | Skill |
| Deterministic lifecycle behavior | Hook |
| Measurable quality standard | Evaluation |
| Missing external capability | Tool/connector |
| Distinct expert role | Agent |
| Repeated process with state/stopping logic | Loop |
| Mutable present condition | State |
| Important choice and rationale | Decision record |
| One-off detail | Conversation only |

## Selection rules

1. Do not persist by default. Persistence has a maintenance cost.
2. Use the smallest adequate primitive.
3. Prefer deterministic mechanisms for deterministic requirements.
4. Prefer progressive disclosure: keep entry instructions small and load detail only when relevant.
5. Separate current truth from reusable procedure.
6. Separate evidence from policy: an observation can justify a candidate without immediately becoming a permanent rule.
7. Design every generated component so it can later be consolidated or retired.

## Evolution cycle

```text
observe
  ↓
identify durable pattern
  ↓
classify
  ↓
check for duplication
  ↓
create candidate
  ↓
try / evaluate
  ↓
promote / revise / reject
  ↓
monitor
  ↓
consolidate / retire
```

## Avoid

- A giant universal prompt.
- Dozens of generic skills loaded for every user.
- A fixed onboarding questionnaire.
- Domain assumptions in the seed.
- Persisting every conversation detail.
- Adding a new permanent rule after every isolated problem.

The seed should remain small enough that cloned instances can diverge substantially according to their objectives.
