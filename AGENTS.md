# AGENTS.md

This repository is a **Harness Designer seed**. Its job is to shape a subject repository into an effective, progressively evolving agent harness. Harness Designer is infrastructure for the subject; it is not the subject repository itself.

## Before bootstrap: establish repository identity

1. Inspect the current Git root, origin/remotes and existing history before changing harness state.
2. Determine whether the current workspace is:
   - the Harness Designer seed/template;
   - an existing subject repository that needs harness initialization; or
   - a subject repository whose harness is already initialized.
3. If an existing or intended subject repository is different from the Harness Designer repository, use `skills/repository-initializer/SKILL.md` before subject bootstrap.
4. The subject repository must remain the sole project Git repository. Preserve its `.git`, origin/remotes, history, README, license and existing project files unless the user explicitly asks otherwise.
5. Treat any Harness Designer clone used during setup as temporary shaping material. Never transplant its `.git` directory or remote into the subject repository.
6. During initialization, leave changes uncommitted and unpushed unless the user explicitly asks for a commit or push.

If repository ownership is genuinely ambiguous and changing Git identity could cause damage, ask one focused question before modifying repository metadata.

## Start of every subject session

1. Read `.harness/manifest.yaml` and `.harness/objective.md`.
2. Follow `hooks/session-start.md`.
3. If `stage: bootstrap`, use `skills/bootstrap/SKILL.md` before inventing domain structure.
4. Load only the skills and knowledge relevant to the current request. Do not dump the entire harness into context.

## Operating rules

- Ask about the **user's objective and work**, not about which harness primitives they want.
- Prefer a few adaptive, high-information questions over a fixed questionnaire.
- Inspect the repository and available tools before asking for information that can be discovered directly.
- It is valid to know the subject while leaving the objective in bootstrap until enough objective context is provided.
- Start useful work as soon as the objective is sufficiently clear; onboarding is not an end in itself.
- Keep this entrypoint small. Put detailed procedures in skills/docs rather than expanding `AGENTS.md` indefinitely.
- Judge harness quality by whether it produces meaningful outcomes for the objective, not merely whether agents follow its instructions.
- Do not treat one successful or failed interaction as sufficient reason to create permanent scaffolding unless it reveals a clear high-consequence invariant.
- When a durable pattern appears during work, use `skills/harness-designer/SKILL.md` to decide whether it belongs in knowledge, instructions, a skill, hook, evaluation, tool, agent, loop or state.
- Prefer the smallest adequate primitive and avoid duplicates.
- Harness changes should be observable and reversible. Candidate changes should be tested before becoming canonical when practical.
- Periodically use `skills/harness-review/SKILL.md` to consolidate, simplify and retire stale assumptions.
- When useful signal exists across multiple trajectories, repeated corrections, accumulated friction or substantial harness growth, use `skills/harness-sleep/SKILL.md`. Prefer a fresh agent/session for this consolidation rather than having the active worker continually rewrite its own environment.
- Never commit credentials, access tokens or secrets into the repository.

## Evolution modes

Harness Designer supports two complementary paths:

- **Online evolution** — high-confidence improvements discovered during active work.
- **Sleep evolution** — offline consolidation across multiple trajectories and outcomes, preferably by a fresh agent perspective.

Do not force either mode on a fixed schedule. Evidence should drive evolution.

## Runtime portability

Files under `hooks/` define lifecycle **contracts**. If the current agent runtime supports native hooks, they may be implemented through an adapter. Otherwise follow the contracts directly at the appropriate lifecycle point.

## End of session

Follow `hooks/session-end.md`. Persist only information that will materially improve future work.
