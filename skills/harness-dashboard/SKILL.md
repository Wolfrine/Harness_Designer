---
name: harness-dashboard
description: Create or evolve an optional subject-specific local dashboard that makes agent sessions, open threads, trajectory evidence and harness evolution visible to the user without making the dashboard itself the source of truth.
---

# Harness Dashboard

Use when the user opts into a Harness Dashboard during bootstrap or asks for one later.

The dashboard is an **observability surface**, not a mandatory part of every harness and not the source of truth for project state. It should be generated for the subject by the working LLM using the minimal design contract in `templates/dashboard/DASHBOARD_SPEC.md`.

## Core principles

1. **User opt-in** — create the dashboard only when the user wants it. It can be enabled or disabled later.
2. **Subject-specific generation** — use the supplied structure as a starting contract, then adapt labels, lanes, metrics and presentation to the actual work.
3. **Trajectory-backed** — prefer durable session/evidence shards under `.harness/trajectory/` when runtime history is insufficient or the dashboard needs persistent history.
4. **Parallel-safe** — prefer one shard per session/agent instead of one shared log file when multiple sessions may run concurrently.
5. **Mechanical capture first** — timestamps, tools, files, branches, skills and similar facts should be captured mechanically when possible. Keep model interpretation such as summaries, outcomes and open threads separate and preserve it across mechanical rewrites.
6. **Local by default** — prefer a self-contained HTML dashboard or similarly portable local artifact that needs no server or CDN unless the subject justifies something stronger.
7. **Privacy-aware** — redact credentials and secrets before persistence. Do not assume that business-sensitive prompts or file names are safe to publish merely because secrets are removed.

## Creation procedure

### 1. Inspect the subject and runtime

Read the objective, manifest, current harness and repository structure. Inspect whether the runtime exposes session hooks, transcripts, conversation history, task metadata or equivalent events.

Decide the least invasive way to obtain useful trajectory evidence.

### 2. Establish the trajectory layer

Use `.harness/trajectory/README.md` as the semantic contract.

Default durable location when needed:

```text
.harness/trajectory/
  sessions/
    <date>-<session-id>.json
```

Use `templates/dashboard/session-shard.example.json` as a starting schema, not a rigid universal format.

If the runtime already provides durable searchable trajectories, do not duplicate them merely to satisfy the template. A dashboard adapter may read the runtime source directly.

### 3. Generate the subject dashboard

Default visible location:

```text
harness-dashboard/
  index.html
```

A builder/generator script may be added beside it when regeneration is useful.

Start from `templates/dashboard/DASHBOARD_SPEC.md`, then adapt the dashboard to what this subject actually needs. Preserve the minimum views unless they clearly provide no value.

### 4. Connect session capture

When native lifecycle hooks exist, create the smallest runtime-specific adapter that updates the current session shard and regenerates the dashboard at useful lifecycle points.

When native hooks do not exist, follow the portable session-end contract and update trajectory evidence only when practical.

Do not require full narrative summaries at every stop. Mechanical session data can exist before model-written interpretation is added.

### 5. Surface harness evolution

The dashboard should make harness evolution visible, using existing canonical sources before adding duplicate logs:

- `.harness/evolution/` candidate/revision/retirement notes;
- `.harness/manifest.yaml` current state and last review/sleep metadata;
- session shards' `harnessChanges` / `harnessEvidence` when available;
- Git history/diffs when useful.

Show what changed, why when known, and whether it came from online evolution, review or sleep consolidation.

### 6. Integrate with sleep

Trajectory evidence should be usable by `skills/harness-sleep/SKILL.md`.

If sleep reviews a set of session shards, it may record lightweight review metadata such as a sleep-cycle id or reviewed timestamp without destroying the original evidence.

### 7. Update manifest

When enabled, record the active dashboard and trajectory locations in `.harness/manifest.yaml`.

When disabled, record the preference so bootstrap does not keep asking. Do not delete historical evidence automatically unless the user asks.

## Minimum validation

Before finishing:

- the dashboard opens locally;
- current sessions/evolution records render without manual edits;
- parallel session files do not contend for one shared write target;
- missing optional fields do not break rendering;
- sensitive credentials are not persisted;
- the dashboard clearly distinguishes observed facts from model-written summaries/interpretation;
- the dashboard can be regenerated from its underlying evidence.

## Outcome

The user should be able to see, at a glance, **what agents have been doing, what remains open, how the harness is changing, and when deeper consolidation has occurred** without reading raw transcripts or harness internals.