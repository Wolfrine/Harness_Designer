# Harness Architecture

Harness Designer separates subject understanding from harness structure. The user should be able to discuss the work naturally; the agent decides what, if anything, deserves persistent structure.

## Repository identity

Harness Designer is a shaping source, not the project identity.

- The subject repository owns `.git`, origin/remotes, history and future project commits.
- Existing subject README, license and project files are preserved unless an intentional edit is required.
- A Harness Designer clone used during setup is temporary and must not leave a nested `.git` or replace the subject remote/history.
- If the subject repository already exists, initialize the harness **into that repository** rather than transforming Harness Designer's Git history into the project.
- If the subject is known but its objective is not, keep the harness in bootstrap instead of fabricating objective details.
- Initialization should default to uncommitted/unpushed changes unless the user explicitly requests repository mutations.

See `skills/repository-initializer/SKILL.md` for the operational procedure.

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
8. Preserve repository identity while evolving harness structure.

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
- Replacing an existing project's Git identity while installing the harness.
- Forcing objective completion when the user has intentionally deferred context.

The seed should remain small enough that initialized subject repositories can diverge substantially according to their objectives.
