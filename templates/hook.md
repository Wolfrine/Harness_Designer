# <Hook Name>

**Event:** <When this hook runs.>

**Purpose:** <What deterministic behavior or guard it provides.>

## Inputs

- <Input/state/tool>

## Behavior

1. <Action>
2. <Action>

## Output / side effects

- <Expected result>

## Failure behavior

Define what should happen when the hook cannot complete. Prefer explicit failure over silently leaving the environment in an unknown state when correctness matters.

## Idempotency

State whether the hook is safe to run more than once and how duplicate effects are prevented.

## Portability

Keep the behavior contract separate from runtime-specific configuration. Add an adapter only when a target runtime needs one.

## Retirement condition

What change in the workflow, tool or runtime would make this hook unnecessary?
