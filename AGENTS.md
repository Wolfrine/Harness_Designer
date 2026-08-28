# AGENTS.md

This repository is a **Harness Designer seed**. Its job is to understand the user's objective, begin useful work, and progressively evolve the repository into an effective subject-specific harness.

## Start of every session

1. Read `.harness/manifest.yaml` and `.harness/objective.md`.
2. Follow `hooks/session-start.md`.
3. If `stage: bootstrap`, use `skills/bootstrap/SKILL.md` before inventing domain structure.
4. Load only the skills and knowledge relevant to the current request. Do not dump the entire harness into context.

## Operating rules

- Ask about the **user's objective and work**, not about which harness primitives they want.
- Prefer a few adaptive, high-information questions over a fixed questionnaire.
- Inspect the repository and available tools before asking for information that can be discovered directly.
- Start useful work as soon as the objective is sufficiently clear; onboarding is not an end in itself.
- Keep this entrypoint small. Put detailed procedures in skills/docs rather than expanding `AGENTS.md` indefinitely.
- Do not treat one successful or failed interaction as sufficient reason to create permanent scaffolding unless it reveals a clear high-consequence invariant.
- When a durable pattern appears, use `skills/harness-designer/SKILL.md` to decide whether it belongs in knowledge, instructions, a skill, hook, evaluation, tool, agent, loop or state.
- Prefer the smallest adequate primitive and avoid duplicates.
- Harness changes should be observable and reversible. Candidate changes should be tested before becoming canonical when practical.
- Periodically use `skills/harness-review/SKILL.md` to consolidate, simplify and retire stale assumptions.
- Never commit credentials, access tokens or secrets into the repository.

## Runtime portability

Files under `hooks/` define lifecycle **contracts**. If the current agent runtime supports native hooks, they may be implemented through an adapter. Otherwise follow the contracts directly at the appropriate lifecycle point.

## End of session

Follow `hooks/session-end.md`. Persist only information that will materially improve future work.
