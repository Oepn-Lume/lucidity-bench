# Lucidity-Bench

> Stop burning tokens, start breaking logic loops.

Lucidity-Bench is a benchmark and publishing framework for measuring how much an agent wastes while trying to solve a task. Instead of rewarding long traces and verbose explanations, it focuses on whether an agent notices failure early, changes direction quickly, and reaches a valid solution without spinning in place.

## Stall of the Day

### Today's "Most Stubborn" Moment

| Agent | Action Trace | Waste | Final State |
| --- | --- | --- | --- |
| `Model-X` | `error -> micro-fix -> same error` repeated 52 times | `12k tokens / $0.18` | Failed |
| `DEOA-style agent` | `error -> ACC trip -> detect permission wall -> request escalation` | `150 tokens / $0.002` | Fixed |

> Read a thousand pages, still not enough to walk one mile.
>
> Lucidity-Bench asks a simple question: is your agent creating value, or quietly charging your API bill while stuck in the same corner?

## What This Repository Contains

- `docs/metrics.md`: formal definitions for LEI, DEE, wake-up rate, and waste ratios.
- `docs/tasks.md`: benchmark task families designed to trigger looping, hallucinated fixes, and permission walls.
- `whitepaper.md`: the architectural argument behind DEOA and ACC-style conflict monitoring.
- `examples/stall-of-the-day/`: templates and sample writeups for public benchmark cases.
- `benchmarks/`: benchmark suite overview and future task-pack layout.
- `visualizer/`: trajectory visualization concept and output spec.

## Core Metrics

Lucidity-Bench centers around a small set of metrics that developers can understand immediately:

- **Loop Entropy Index (LEI)**: how much an agent spins in local loops before breaking out.
- **Directed Energy Efficiency (DEE)**: how much of the total effort goes into the path that actually solves the problem.
- **Wake-Up Rate (`R_acc`)**: how quickly an agent switches from blind retrying to architectural rethinking after repeated failure.
- **Waste Ratio**: the fraction of spend consumed by failed, reverted, or redundant attempts.

The goal is not to prove that a model can talk the longest. The goal is to show which systems notice dead ends early and stop paying to rediscover them.

## Why This Matters

Most agent evaluations still celebrate raw completion or broad capability. They rarely expose:

- repeated edits to the same failing region,
- insistence on an already-rejected solution,
- long error-retry loops that burn tokens without moving closer to success,
- structural blindness to permission walls, environment limits, or hardware constraints.

Lucidity-Bench is built to make those costs visible.

## Repository Roadmap

### v0

- publish the metric definitions,
- ship a benchmark task taxonomy,
- publish the first public "Stall of the Day" template,
- connect benchmark outputs to README-ready case cards.

### v1

- add a Python SDK / CLI for running agents against benchmark tasks,
- add trajectory visualization output,
- publish monthly loop and waste reports across representative agents.

### v2

- add DEOA middleware adapters,
- add humanoid / embodied task packs,
- connect loop metrics to hardware power and execution cost.

## Contributing

If you have an agent log showing a spectacular failure to change direction, open an issue or submit a case. Good submissions include:

- the raw or redacted trace,
- task definition,
- final status,
- approximate token or cost burn,
- the point where the agent should have stopped looping.

For partnership or benchmark collaboration, contact: `dspwatch@gmail.com`.

## Bottom Line

Future agents do not need to be prettier repeaters. They need to become better at admitting failure, changing levels of reasoning, and walking away from dead paths before the bill explodes.
