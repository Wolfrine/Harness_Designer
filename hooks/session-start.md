# Session Start Hook Contract

**Event:** beginning of a new agent session or materially new work thread.

**Purpose:** establish repository identity when necessary, then reconstruct only the context needed for the current request and route the session into the right part of the harness.

## Behavior

1. Confirm whether the current workspace is the Harness Designer seed, a subject repository awaiting initialization, or an already initialized subject repository.
2. If repository ownership is not yet established, or the user identifies a different existing subject repository, use `skills/repository-initializer/SKILL.md` before subject bootstrap.
3. In an initialized subject repository, read `.harness/manifest.yaml` and `.harness/objective.md`.
4. Determine whether the subject remains in bootstrap or is already active.
5. If repository-local trajectory evidence is enabled, initialize or continue the current session's independent trajectory shard using mechanically available runtime/session metadata. Do not fabricate unavailable fields or require model-written summary fields at session start.
6. Understand the current user request and classify its immediate work mode, for example:
   - discovery/exploration;
   - analysis/research;
   - creation/implementation;
   - debugging/issue resolution;
   - planning/decision support;
   - operation/maintenance;
   - harness/meta work.
7. Inspect available repository context and tools before asking for missing information.
8. Load only the skills, knowledge and state that materially help this request.
9. If subject bootstrap is required, invoke `skills/bootstrap/SKILL.md`. Bootstrap resolves the optional Harness Dashboard preference when still undecided.
10. If the request concerns improving the working environment itself, load `skills/harness-designer/SKILL.md`.
11. If the request concerns the enabled dashboard/trajectory layer, load `skills/harness-dashboard/SKILL.md`.
12. Surface blocking uncertainty to the user only when it cannot reasonably be resolved from available context or through safe progress.

## Trajectory start behavior

When local trajectory capture is active:

- prefer one shard per independent runtime session/agent;
- record session id, start timestamp, branch/workspace and opening direction when available;
- allow the shard to be incomplete until session end;
- never put credentials/secrets into the shard;
- do not make trajectory capture block the actual work if the runtime cannot provide metadata cleanly.

## Repository identity invariant

Once a subject repository is established, it remains the sole project Git repository unless the user explicitly requests a repository migration. Harness Designer must not replace its `.git`, origin, history, README or license as a side effect of harness setup.

## Output

The hook should leave the agent with:

- confidence about which repository owns the project;
- a concise understanding of the current objective;
- the likely work mode;
- the relevant harness components to use;
- important current state/constraints;
- an initialized trajectory record when that capability is enabled and practical;
- no unnecessary context payload.

## Native implementation

A runtime-specific adapter may automate parts of this contract. The portable contract remains the source of intent.
