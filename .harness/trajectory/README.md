# Trajectory / Evidence

This directory defines the optional durable evidence layer for agent work.

A **trajectory** records what actually happened during work: what an agent/session attempted, what tools or skills it used, what it touched, what outcome occurred, what corrections appeared and what harness evidence emerged.

Trajectory evidence is different from:

- **Knowledge** — reusable facts/reference material;
- **State** — what is true now;
- **Evaluation** — how quality is judged;
- **Decision records** — important choices and rationale.

Trajectory evidence is historical experience that can later support continuation, observability, evaluation and sleep consolidation.

## Use only when useful

Do not create repository-local trajectory logging merely because Harness Designer supports it.

Use it when the subject benefits from durable cross-session visibility, parallel-agent history, transcript retention beyond the runtime window, evidence-backed harness evolution or an opted-in Harness Dashboard.

If the runtime already exposes durable searchable trajectories sufficient for these purposes, reference or adapt that source instead of duplicating it.

## Preferred repository-local shape

When local persistence is justified:

```text
.harness/trajectory/
  sessions/
    <date>-<session-id>.json
```

Prefer one shard per independent session/agent. This avoids write contention when multiple agents work in parallel and lets individual evidence records be rebuilt or enriched independently.

`templates/dashboard/session-shard.example.json` provides a starting shape. Subjects may extend or simplify it.

## Mechanical vs interpreted evidence

Prefer mechanical/runtime capture for facts such as:

- session id and timestamps;
- branch/workspace;
- prompts or opening direction when appropriate;
- tools/connectors and counts;
- files touched;
- skills/sub-agents used;
- Git/harness files changed.

Keep model-written interpretation distinct, for example:

- concise summary;
- outcome assessment;
- open continuation point;
- user correction interpretation;
- harness-improvement evidence.

Mechanical rewrites should preserve existing model-written fields rather than erase them.

## Harness evolution

When a session exposes a possible harness-level pattern, record only enough evidence to let future work or sleep consolidation find it. Do not turn every observation into a permanent harness rule.

When a sleep cycle reviews trajectory shards, it may attach lightweight review metadata such as a cycle id or reviewed timestamp while preserving the original record.

## Security

Redact credentials, secrets, bearer tokens, PATs and comparable sensitive values before persistence.

Trajectory data can still contain confidential subject information. Treat repository-local evidence according to the subject repository's privacy requirements.

## Consumers

Trajectory evidence may be consumed by:

- future agents continuing related work;
- `skills/harness-sleep/SKILL.md`;
- evaluations and harness reviews;
- an optional user-facing Harness Dashboard generated through `skills/harness-dashboard/SKILL.md`.
