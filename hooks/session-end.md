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
8. If harness structure changed, update `.harness/manifest.yaml` and relevant references.
9. Do not generate a session summary, timeline entry or memory artifact merely because the session ended. Add such mechanisms only if this subject benefits from them.

## Output

The next session should be able to continue important work without carrying the entire previous conversation, while meaningful evidence remains available for later harness consolidation when warranted.

## Principle

**Continuity is useful; indiscriminate logging and continuous self-patching are not.**
