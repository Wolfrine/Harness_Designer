# Harness Dashboard — Generation Contract

This is a **starting contract for the LLM**, not a fixed dashboard implementation. Generate a dashboard suited to the subject while preserving the useful observability concepts below.

## Purpose

Give the user a human-readable view of:

- what agent sessions have happened;
- what those sessions were trying to accomplish;
- what remains open;
- which tools, skills, files and sub-agents were involved when useful;
- how the harness itself has changed over time;
- when review or sleep consolidation occurred.

The dashboard is a view over canonical evidence. It must not become the only place where important state exists.

## Recommended information architecture

### 1. Overview

Useful starting indicators include:

- indexed sessions;
- active days;
- open threads;
- recent harness changes;
- current harness stage/version;
- last harness review;
- last sleep cycle.

Choose only indicators meaningful for the subject.

### 2. Activity navigator

Provide a compact time-based view such as a day heatmap or equivalent so users can navigate periods of activity.

### 3. Session timeline

Each session should be inspectable without opening the raw transcript. Useful fields include:

- title / opening direction;
- timestamp and duration when known;
- task/work type;
- branch/workspace when relevant;
- concise summary or outcome when available;
- open continuation point;
- notable tools/connectors;
- skills and sub-agents;
- files touched;
- harness evidence or harness changes produced by the session.

Do not force unavailable fields.

### 4. Parallel-work view

If the subject commonly uses multiple parallel agents/sessions, provide a swimlane, thread grouping, fork grouping or other visual that makes concurrency understandable.

If parallel work is rare, omit this rather than creating decorative complexity.

### 5. Harness evolution

Provide a dedicated view/feed for changes to the working environment itself. Derive from existing evidence such as:

- `.harness/evolution/` notes;
- manifest changes;
- trajectory `harnessChanges` fields;
- Git history/diffs;
- review/sleep metadata.

Useful categories can include:

- candidate created;
- instruction/skill/hook/tool/agent/loop/state added or revised;
- component simplified/merged/retired;
- evaluation added or changed;
- dashboard/trajectory capability changed;
- sleep cycle completed.

Where evidence exists, show the reason or trajectory references that justified the change.

### 6. Search and filters

Allow practical discovery across session title/direction, summary, open thread, files, tools, skills, agent type and harness-change evidence.

## Data expectations

Preferred optional durable source:

```text
.harness/trajectory/sessions/*.json
```

Additional canonical inputs may include:

```text
.harness/manifest.yaml
.harness/evolution/
Git history
runtime-native trajectory stores
```

Use one session shard per independent session/agent when writing repository-local evidence so parallel work does not create avoidable write conflicts.

## Presentation

Prefer:

- a self-contained local HTML page with no CDN or server dependency;
- clear light/dark behavior where practical;
- compact, information-dense cards rather than decorative UI;
- subject-specific labels and categories;
- graceful handling of incomplete historical data.

The LLM may generate a builder script when regeneration from many shards is useful. The generated artifact should remain inspectable and easy to open.

## Fact vs interpretation

Visually or structurally distinguish:

**Mechanical evidence** — session id, timestamps, branch, tool counts, files, skill names, Git changes.

**Model-written interpretation** — summary, outcome assessment, open thread, correction interpretation, harness-evolution rationale.

A mechanical rebuild must preserve model-written fields already present in the source shards.

## Security

Redact credentials, bearer tokens, PATs, secrets and comparable sensitive values before persistence.

A local dashboard may still contain confidential business material. Do not publish or expose it externally without explicit intent.

## Success condition

A user who has not followed every agent chat should be able to open the dashboard and understand:

1. what work has happened;
2. what work is still unresolved;
3. where parallel or repeated work occurred;
4. how the harness has evolved because of that experience;
5. when the harness was last consolidated/reviewed.