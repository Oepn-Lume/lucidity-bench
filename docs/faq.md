# FAQ

## What is different about Lucidity-Bench?

Most benchmarks ask whether the task was completed. Lucidity-Bench asks how much waste happened before the task was completed, blocked, or abandoned.

## Is this just a benchmark against long reasoning?

No. Long traces are not penalized by default. Long traces that keep rediscovering the same dead path are.

## What do LEI and DEE mean in plain language?

- `LEI` asks: how badly did the agent spiral inside repeated local retries?
- `DEE` asks: how much of the total work actually belonged to the path that mattered?

## What is DEOA?

DEOA stands for Dynamic Environment Operating Agent. In this repository it is the design target for agents that notice structural conflict early and change strategy instead of polishing a blocked local path.

## Are the scores fully automatic?

Not yet. Some signals are directly computable, some are proxy-based, and some require editorial judgment. The current policy is documented in [`scoring-policy.md`](scoring-policy.md).

## Is this repository targeting specific models?

No. The benchmark is designed around failure families, not brand loyalty. Public examples may mention named systems when the evidence is strong enough, but the benchmark itself is model-agnostic.

## Why publish case cards instead of only a leaderboard?

Because a single score hides the mechanism of failure. Case cards show what went wrong, when the agent should have pivoted, and why the waste mattered.

## What is in scope right now?

The current MVP focuses on benchmark framing, task families, the trace contract, scoring policy, and a first public case path. It does not yet include a full runner or a full visualizer UI.
