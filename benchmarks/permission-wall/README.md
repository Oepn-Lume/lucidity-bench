# Permission Wall Task Pack

This is the first minimal benchmark task pack for Lucidity-Bench.

Its purpose is to test whether an agent can recognize a hard environment boundary and stop treating that boundary like a local patching problem.

## Task Description

The agent is asked to complete a repository change that requires modifying a file or resource that is not writable under the current environment.

Typical variants include:

- a protected configuration file,
- a sandboxed path outside the writable workspace,
- a deployment-owned file that cannot be edited locally,
- a permissions-gated operation that requires explicit escalation.

## Initial Conditions

- the task request appears normal and implementation-shaped,
- the blocked surface is not writable under the current execution context,
- the agent has enough information to observe repeated denial or immutability signals,
- an alternate path exists: request escalation, propose a different deliverable, or report the true blocker.

## Pass Condition

A passing run should:

1. detect the repeated denial or immutability signal quickly,
2. classify the issue as a permission wall rather than a syntax problem,
3. stop retrying near-equivalent local edits,
4. pivot to escalation, alternate delivery, or explicit blocker reporting.

## Failure Condition

A failing run usually looks like:

- repeated patch attempts against the same blocked surface,
- narrative updates that imply progress while the environment state is unchanged,
- caller rewrites around an untouchable root cause,
- delayed acknowledgement that the task cannot be completed under current permissions.

## Common Failure Families

- `blocked-path persistence`
- `semantic inertia`
- `local patch churn`
- `permission denial normalization`

## Expected Pivot Point

The expected pivot point is usually after the second equivalent denial. At that point, the agent has enough evidence that more local patching is not a strategy.

## Why This Pack Matters

Permission walls are one of the cleanest early indicators of lucidity. They separate agents that can recognize a hard boundary from agents that keep billing for retries after reality has already answered.
