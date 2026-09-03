# Session End Hook Contract

**Event:** end of a meaningful work session or before context is likely to be lost.

**Purpose:** preserve useful continuity and surface harness-improvement evidence without turning every session into permanent scaffolding.

## Behavior

1. Verify the work completed in this session to the extent practical.
2. Identify outcomes future sessions genuinely need:
   - current state;
   - decisions and rationale;
   - unresolved blockers;
   - newly reliable domain knowledge.
3. Persist only those outcomes in an appropriate location when persistence provides future value.
4. Ask internally whether the session exposed meaningful harness evidence such as:
   - repeated manual work;
   - recurring friction;
   - a missing capability;
   - a stable user/work principle;
   - an invariant that should be enforced;
   - a useful quality criterion;
   - a process that may deserve recurrence or specialization;
   - an unexpectedly strong strategy worth understanding;
   - a correction that may recur.
5. For a clear high-confidence durable improvement, apply `skills/harness-designer/SKILL.md` directly when justified.
6. Otherwise preserve or surface the evidence only where useful so it can be compared with later trajectories. Do not mutate the harness merely because one session was imperfect.
7. When evidence has accumulated across multiple sessions/agents, or the harness itself has become difficult to reason about, prefer `skills/harness-sleep/SKILL.md` for offline consolidation by a fresh agent/session.
8. If repository-local trajectory evidence is enabled, update the current session shard with mechanically available facts and preserve existing model-written fields. Record concise `harnessEvidence` / `harnessChanges` only when real harness-level evidence or changes occurred.
9. If the optional Harness Dashboard is enabled, refresh/regenerate it at an appropriate lifecycle point using `skills/harness-dashboard/SKILL.md` or its generated runtime adapter. Do not make dashboard regeneration block important subject work when it can safely be deferred to the next lifecycle event.
10. If harness structure changed, update `.harness/manifest.yaml` and relevant references.
11. Do not generate a session summary, timeline entry, trajectory shard or dashboard merely because the session ended when observability/trajectory persistence is disabled and the subject has no demonstrated need for it.

## Trajectory handling

When trajectory persistence is enabled:

- prefer one shard per session/agent;
- mechanically capture timestamps, branch/workspace, tools/connectors, files touched, skills and sub-agents when available;
- keep model-written summary/outcome/open-thread/correction fields separate;
- preserve those model-written fields across mechanical rewrites;
- redact credentials and secrets before persistence;
- allow incomplete shards rather than fabricating unavailable data.

## Output

The next session should be able to continue important work without carrying the entire previous conversation, while meaningful evidence remains available for later harness consolidation when warranted.

When the user opted into a dashboard, the user should also be able to see the completed session and any material harness evolution without reading raw transcripts.

## Principle

**Continuity and observability are useful; indiscriminate logging and continuous self-patching are not.**
