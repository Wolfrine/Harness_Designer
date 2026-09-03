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
| Durable record of what agents actually did/outcomes | Trajectory / evidence |
| Important choice and rationale | Decision record |
| One-off detail | Conversation only |

## Selection rules

1. Do not persist by default. Persistence has a maintenance cost.
2. Use the smallest adequate primitive.
3. Prefer deterministic mechanisms for deterministic requirements.
4. Prefer progressive disclosure: keep entry instructions small and load detail only when relevant.
5. Separate current truth from reusable procedure.
6. Separate evidence from policy: an observation can justify a candidate without immediately becoming a permanent rule.
7. Separate historical trajectory from current state: what happened before is evidence, not automatically current truth.
8. Design every generated component so it can later be consolidated or retired.
9. Preserve repository identity while evolving harness structure.
10. Judge improvement by objective outcomes, not instruction compliance alone.

## Trajectory / evidence layer

Trajectory evidence is the historical record of what agents actually attempted and what happened. It becomes useful when a project needs cross-session continuity, parallel-agent visibility, durable history beyond runtime transcript retention, evidence-backed sleep consolidation or a user-facing Harness Dashboard.

When repository-local persistence is justified, prefer independent session shards such as:

```text
.harness/trajectory/sessions/<date>-<session-id>.json
```

One shard per session/agent reduces write conflicts during parallel work.

Prefer mechanical capture for timestamps, tools, files, branches, skills and similar observable facts. Keep model-written interpretation — summaries, outcomes, open threads and harness evidence — distinct and preserve it across mechanical rewrites.

Do not require local trajectory logging if the runtime already provides sufficient durable searchable evidence.

See `.harness/trajectory/README.md`.

## Optional Harness Dashboard

During bootstrap the user is asked once whether they want a local Harness Dashboard.

If enabled, `skills/harness-dashboard/SKILL.md` uses `templates/dashboard/DASHBOARD_SPEC.md` as a minimal generation contract and the LLM creates a subject-specific dashboard rather than installing a rigid universal UI.

The dashboard may visualize:

- sessions and activity over time;
- open continuation points;
- parallel/forked work when relevant;
- tools, skills, sub-agents and files used;
- harness changes and candidate evolution;
- review and sleep consolidation history.

The dashboard is a view over canonical evidence, not the source of truth itself.

## Evolution architecture

Harness Designer supports two complementary evolutionary modes.

### Online evolution

Use during active work when a high-confidence durable improvement is obvious.

```text
observe
  ↓
identify durable pattern
  ↓
classify
  ↓
check for duplication
  ↓
create candidate when needed
  ↓
try / evaluate
  ↓
promote / revise / reject
```

### Sleep evolution

Use offline when useful signal emerges across multiple trajectories or when the harness itself needs consolidation.

```text
AWAKE
  ↓
agents perform real work
  ↓
trajectories / outcomes / corrections accumulate
  ↓
enough adaptation pressure
  ↓
SLEEP
  ↓
fresh agent reconstructs objective + harness
  ↓
review several recent trajectories
  ↓
judge meaningful outcomes
  ↓
abstract cross-run patterns
  ↓
consolidate / simplify / retire
  ↓
generate candidate harness mutations
  ↓
evaluate / regression-check
  ↓
promote useful changes
  ↓
WAKE with evolved harness
```

The sleep consolidator should preferably be a fresh agent or session rather than the worker that produced the recent trajectories. This reduces attachment to local reasoning paths and creates a clean separation between performing work and improving the system that performs it.

Sleep should consume evidence already available from conversations, runtime trajectories, `.harness/trajectory/` when enabled, Git history, evaluations, user feedback and evolution notes before inventing new logging infrastructure.

During sleep, candidate harness changes should be isolated from unrelated real-world subject actions when practical. The system may inspect, reason, simulate and test without granting experimental behavior unnecessary production authority.

See `skills/harness-sleep/SKILL.md` for the operational procedure.

## Avoid

- A giant universal prompt.
- Dozens of generic skills loaded for every user.
- A fixed onboarding questionnaire.
- Domain assumptions in the seed.
- Persisting every conversation detail.
- Adding a new permanent rule after every isolated problem.
- Continuous self-editing by the active agent when evidence should first accumulate across runs.
- Mandatory trajectory bureaucracy when existing runtime evidence is sufficient.
- Treating a dashboard as canonical state.
- Creating a dashboard after the user explicitly declined it.
- Replacing an existing project's Git identity while installing the harness.
- Forcing objective completion when the user has intentionally deferred context.

The seed should remain small enough that initialized subject repositories can diverge substantially according to their objectives.
