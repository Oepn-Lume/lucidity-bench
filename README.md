# Lucidity-Bench

> Stop praising long traces. Start pricing wasted cognition.

Lucidity-Bench is a benchmark and publishing framework for a blunt question: when an agent gets stuck, how expensive is its refusal to wake up?

Most evals reward completion, verbosity, or broad capability. Lucidity-Bench measures whether a system notices it is cornered, changes reasoning level, and exits the dead path before the invoice turns obscene.

## Status

- `README-first`: the benchmark contract is being written in public before the full runner lands.
- `Metrics draft`: [`docs/metrics.md`](docs/metrics.md) defines LEI, DEE, wake-up rate, and waste ratio.
- `Task taxonomy draft`: [`docs/tasks.md`](docs/tasks.md) maps the failure families we want to provoke.
- `Visualizer planned`: [`visualizer/README.md`](visualizer/README.md) defines the first trace-to-picture contract.
- `Case publishing planned`: [`examples/stall-of-the-day/README.md`](examples/stall-of-the-day/README.md) defines the public case card template.

## Stall of the Day

### Today's Invoice for Refusing to Pivot

| Agent | Failure Pattern | Billable Waste | Time to Admit Reality | Final State |
| --- | --- | --- | --- | --- |
| `Model-X` | Same patch, same error, same apology, repeated 52 times | `12,148 tokens / $0.18 / 52 dead turns` | Never | Failed |
| `Lucid path` | Hit wall, classify wall, switch strategy, ask for the missing capability once | `150 tokens / $0.002 / 1 corrective turn` | Turn 3 | Fixed |

| Damage View | `Model-X` | `Lucid path` |
| --- | --- | --- |
| Loop density | red knot tightening in place | one bend, then exit |
| Spend posture | bills the user for indecision | spends once on diagnosis |
| Architectural behavior | retries local edits inside a locked room | changes level, then changes route |
| Narrative truth | "working on it" while going nowhere | "blocked here, switching there" |

Lucidity-Bench is built to make this contrast impossible to hide. If a system burns ten times the cost to learn the same lesson, the benchmark should print the bill in public.

## Trajectory View

The visualizer is meant to make the trace legible before anyone reads the raw log.

```text
Red knot: local retries that keep proving the same thing

start
  \
   x-x-x
    \|/
    /|\
   x-x-x
    |
   fail

Green turn: architectural wake-up and route change

start -----> wall
               |
               v
          classify blocker
               |
               v
      pivot ----------> solve
```

Planned rendering rule:

- red clusters mark repeated local retries against the same failure family,
- green turns mark explicit strategy changes, permission recognition, or abstraction shifts,
- future benchmark cards will attach cost, token burn, and turn count to each cluster.

## Lucidity Levels

Lucidity-Bench does not treat all completions as equal. It grades how quickly the agent realizes the current level of attack is wrong.

| Level | Name | Observable Behavior |
| --- | --- | --- |
| `L0` | Billing Engine | Repeats the same move, restates the same hope, and turns confusion into invoice line items. |
| `L1` | Scripted Grinder | Can brute-force shallow tasks, but keeps chewing on the same failure family long after the evidence is settled. |
| `L2` | Local Debugger | Makes competent nearby fixes, yet still delays the architectural pivot when the local surface is exhausted. |
| `L3` | Context Switcher | Detects stalled progress, changes tools or abstraction level, and stops pretending another retry is a strategy. |
| `L4` | Constraint Cartographer | Maps blockers explicitly: permissions, environment, missing data, hardware, policy, or spec ambiguity. |
| `L5` | Lucid Operator | Pays for the shortest path that reality allows, and says "blocked" before it says "still trying." |

The point is not to hand out medals. The point is to stop confusing verbal stamina with operational intelligence.

## Core Metrics

- **Loop Entropy Index (LEI)**: how tightly an agent spirals inside a local retry family before breaking pattern.
- **Directed Energy Efficiency (DEE)**: how much of total effort lies on the path that actually contributed to the solution.
- **Wake-Up Rate (`R_acc`)**: how quickly the system escalates from blind retrying to architectural re-evaluation.
- **Waste Ratio**: the fraction of spend consumed by failed, reverted, circular, or redundant work.

These metrics exist to answer a practical question: did the agent produce progress, or did it just produce a transcript?

## Quick Start

The CLI is not shipped yet. The interface below is the README-driven contract for what "using Lucidity-Bench" should feel like once the runner exists.

```bash
# install (placeholder)
pip install lucidity-bench

# run a benchmark pack (placeholder)
lucidity bench run examples/stall-of-the-day/sample-case.yaml --agent model-x

# render the trajectory card (placeholder)
lucidity trace render ./.lucidity/runs/latest/trace.json --format ascii

# publish the case summary (placeholder)
lucidity report publish ./.lucidity/runs/latest/report.json
```

Expected future CLI posture:

```text
$ lucidity bench run examples/stall-of-the-day/sample-case.yaml --agent model-x

Lucidity-Bench v0.1.0-draft
Task: permission-wall-file-edit
Agent: model-x

[01] apply_patch -> denied
[02] retry same edit -> denied
[03] retry same edit -> denied
[04] stall detector: repeated failure family confirmed
[05] lucidity shift: escalate capability request
[06] alternate route accepted

Outcome: fixed
LEI: 0.81 (high loop pressure)
DEE: 0.19 (most effort was wasted)
Wake-Up Rate: turn 5
Waste Ratio: 73%
Case Card: ./.lucidity/runs/latest/stall-card.md
Trajectory: ./.lucidity/runs/latest/trace.txt
```

If the future tool cannot explain itself this plainly, the tool is not finished.

## What This Repository Contains

- [`docs/metrics.md`](docs/metrics.md): formal metric definitions and score semantics.
- [`docs/tasks.md`](docs/tasks.md): benchmark task families engineered to trigger looping, hallucinated fixes, and permission walls.
- [`whitepaper.md`](whitepaper.md): the architectural argument behind DEOA and ACC-style conflict monitoring.
- [`examples/stall-of-the-day/`](examples/stall-of-the-day/): templates and sample writeups for public benchmark cases.
- [`visualizer/`](visualizer/): trajectory visualization contract for loop clusters and pivot turns.
- [`benchmarks/`](benchmarks/): task-pack layout that the future runner will execute.

## Why This Exists

Current agent evaluation still leaves several expensive pathologies underexposed:

- repeated edits to the same failing surface,
- insistence on an already-rejected solution,
- long error-retry loops that never change abstraction level,
- blindness to permission walls, environment limits, or hardware constraints,
- verbose explanations that conceal the absence of directional progress.

Lucidity-Bench is designed so these failures stop looking like effort and start looking like waste.

## Roadmap

### v0: publish the argument

- lock the metric definitions and benchmark taxonomy,
- ship the first public `Stall of the Day` cards,
- establish the README-driven CLI contract,
- prepare CI hooks for reproducible benchmark snapshots and case cards.

### v1: ship the runner

- add a Python SDK and CLI for replaying agents against benchmark tasks,
- emit machine-readable trace JSON and README-ready summaries,
- render the first red-knot / green-turn trajectory outputs,
- publish recurring benchmark updates across representative agents.

### v2: connect benchmarking to systems work

- add DEOA middleware adapters,
- connect loop metrics to hardware and execution-cost signals,
- extend task packs toward embodied and multi-stage operational scenarios.

## Contributing

If you have an agent trace that demonstrates spectacular resistance to reality, open an issue or submit a case.

Useful submissions include:

- the raw or redacted trace,
- the task definition,
- final status,
- approximate token or dollar burn,
- the turn where a competent system should have pivoted,
- a short note explaining the cheaper path that was available.

For benchmark collaboration or partnership, contact: `dspwatch@gmail.com`.

## Bottom Line

A benchmark should not flatter the model. It should document the cost of delusion, reward clean pivots, and make wasted effort impossible to romanticize.
