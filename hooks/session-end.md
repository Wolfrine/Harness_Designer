# Session End Hook Contract

**Event:** end of a meaningful work session or before context is likely to be lost.

**Purpose:** preserve useful continuity and notice harness-improvement opportunities without turning every session into permanent scaffolding.

## Behavior

1. Verify the work completed in this session to the extent practical.
2. Identify outcomes future sessions genuinely need:
   - current state;
   - decisions and rationale;
   - unresolved blockers;
   - newly reliable domain knowledge.
3. Persist only those outcomes in an appropriate location when persistence provides future value.
4. Ask internally whether the session exposed:
   - repeated manual work;
   - recurring friction;
   - a missing capability;
   - a stable user/work principle;
   - an invariant that should be enforced;
   - a useful quality criterion;
   - a process that may deserve recurrence or specialization.
5. If yes, apply `skills/harness-designer/SKILL.md`. Prefer a candidate change when the evidence is still weak.
6. If harness structure changed, update `.harness/manifest.yaml` and relevant references.
7. Do not generate a session summary, timeline entry or memory artifact merely because the session ended. Add such mechanisms only if this subject benefits from them.

## Output

The next session should be able to continue important work without carrying the entire previous conversation.

## Principle

**Continuity is useful; indiscriminate logging is not.**
