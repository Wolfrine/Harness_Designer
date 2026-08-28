# Session Start Hook Contract

**Event:** beginning of a new agent session or materially new work thread.

**Purpose:** reconstruct only the context needed for the current request and route the session into the right part of the harness.

## Behavior

1. Read `.harness/manifest.yaml` and `.harness/objective.md`.
2. Determine whether the clone is still in bootstrap or already active.
3. Understand the current user request and classify its immediate work mode, for example:
   - discovery/exploration;
   - analysis/research;
   - creation/implementation;
   - debugging/issue resolution;
   - planning/decision support;
   - operation/maintenance;
   - harness/meta work.
4. Inspect available repository context and tools before asking for missing information.
5. Load only the skills, knowledge and state that materially help this request.
6. If bootstrap is required, invoke `skills/bootstrap/SKILL.md`.
7. If the request concerns improving the working environment itself, load `skills/harness-designer/SKILL.md`.
8. Surface blocking uncertainty to the user only when it cannot reasonably be resolved from available context or through safe progress.

## Output

The hook should leave the agent with:

- a concise understanding of the current objective;
- the likely work mode;
- the relevant harness components to use;
- important current state/constraints;
- no unnecessary context payload.

## Native implementation

A runtime-specific adapter may automate parts of this contract. The portable contract remains the source of intent.
