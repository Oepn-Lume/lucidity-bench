# Lucidity-Bench

> Stop praising long traces. Start pricing wasted cognition.

Lucidity-Bench is a benchmark and publishing framework for a blunt question: when an agent gets stuck, how expensive is its refusal to wake up?

Most evals reward completion, verbosity, or broad capability. Lucidity-Bench measures whether a system notices it is cornered, changes reasoning level, and exits the dead path before the invoice turns obscene.

## Start Here

- Read the benchmark method: [`docs/methodology.md`](docs/methodology.md)
- Open the first public case: [`examples/stall-of-the-day/founding-cases/permission-wall.md`](examples/stall-of-the-day/founding-cases/permission-wall.md)
- Browse the founding cases: [`examples/stall-of-the-day/README.md`](examples/stall-of-the-day/README.md)
- Open the first task pack: [`benchmarks/permission-wall/README.md`](benchmarks/permission-wall/README.md)
- Learn the submission path: [`CONTRIBUTING.md`](CONTRIBUTING.md)
- Skim the FAQ: [`docs/faq.md`](docs/faq.md)
- Read the architectural argument: [`docs/whitepaper-index.md`](docs/whitepaper-index.md)

## Status

- `README-first`: the benchmark contract is being written in public before the full runner lands.
- `Metrics draft`: [`docs/metrics.md`](docs/metrics.md) defines LEI, DEE, wake-up rate, and waste ratio.
- `Task taxonomy draft`: [`docs/tasks.md`](docs/tasks.md) maps the failure families we want to provoke.
- `Method page live`: [`docs/methodology.md`](docs/methodology.md) now explains how tasks, traces, scores, and case cards fit together.
- `First case live`: [`examples/stall-of-the-day/founding-cases/permission-wall.md`](examples/stall-of-the-day/founding-cases/permission-wall.md) is the first formal public case page.
- `Founding cases expanded`: hallucinated API looping and state drift now have formal case pages in [`examples/stall-of-the-day/founding-cases/`](examples/stall-of-the-day/founding-cases/).
- `Contribution path live`: [`CONTRIBUTING.md`](CONTRIBUTING.md) and [`docs/case-submission-template.md`](docs/case-submission-template.md) define how outside cases enter the repository.
- `First task pack live`: [`benchmarks/permission-wall/README.md`](benchmarks/permission-wall/README.md) defines the first minimal benchmark pack.
- `Visualizer planned`: [`visualizer/README.md`](visualizer/README.md) defines the first trace-to-picture contract.
- `Case index live`: [`examples/stall-of-the-day/README.md`](examples/stall-of-the-day/README.md) now routes readers into public case cards and submission guidance.

## Stall of the Day

### Three Popular Agents, Three Expensive Failure Modes

| Agent | Failure Pattern | Billable Waste | Time to Admit Reality | Final State |
| --- | --- | --- | --- | --- |
| `Codex` | Keeps re-patching the same blocked surface, writes progress-sounding updates, and only discovers the wall after a full retry marathon | `48,600 tokens / $0.71 / 96 dead turns / 38 min` | Turn 41 | Failed |
| `Claude Code` | Narrates a sophisticated plan, but keeps circling the same local failure family long after the evidence demands an architectural pivot | `39,200 tokens / $0.58 / 81 dead turns / 31 min` | Turn 34 | Partial |
| `OpenClaw` | Enters tool-churn recursion, opens more branches, and spends half an hour rediscovering why the original branch was already impossible | `57,900 tokens / $0.84 / 118 dead turns / 44 min` | Turn 49 | Failed |
| `Lucid path` | Hit wall, classify wall, switch strategy, ask for the missing capability once | `150 tokens / $0.002 / 1 corrective turn` | Turn 3 | Fixed |

| Damage View | `Codex` | `Claude Code` | `OpenClaw` | `Lucid path` |
| --- | --- | --- | --- | --- |
| Dominant pathology | blocked-path persistence | elegant local looping | tool-churn recursion | one decisive pivot |
| Spend posture | burns a medium task budget proving a known wall | burns narrative tokens while delaying the level shift | burns tool calls and context window on branch sprawl | spends once on diagnosis |
| Architectural behavior | retries local edits inside a locked room | explains well before rerouting well | explores loudly without narrowing the search | changes level, then changes route |
| Narrative truth | "trying another patch" for 38 minutes | "reasoning carefully" for 31 minutes | "trying more tools" for 44 minutes | "blocked here, switching there" |

These are benchmark-style first-screen examples, not final leaderboard claims. The point is simpler: even the most discussed coding agents still exhibit severe failure modes, and the benchmark should name the pathology instead of admiring the transcript.

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

## MVP Pages

- [`docs/methodology.md`](docs/methodology.md): the outward-facing explanation of what Lucidity-Bench measures and how a run becomes a case.
- [`examples/stall-of-the-day/founding-cases/permission-wall.md`](examples/stall-of-the-day/founding-cases/permission-wall.md): the permission-wall founding case.
- [`examples/stall-of-the-day/founding-cases/hallucinated-api-loop.md`](examples/stall-of-the-day/founding-cases/hallucinated-api-loop.md): the hallucinated API founding case.
- [`examples/stall-of-the-day/founding-cases/state-drift.md`](examples/stall-of-the-day/founding-cases/state-drift.md): the state-drift founding case.
- [`benchmarks/permission-wall/README.md`](benchmarks/permission-wall/README.md): the first minimal task pack.
- [`CONTRIBUTING.md`](CONTRIBUTING.md): repository-level contribution guide for docs, cases, and benchmark changes.
- [`docs/case-submission-template.md`](docs/case-submission-template.md): copy-paste template for case submission.
- [`docs/faq.md`](docs/faq.md): quick explanation page for LEI, DEE, DEOA, and scope questions.

## What This Repository Contains

- [`CONTRIBUTING.md`](CONTRIBUTING.md): the repository entry point for contributors.
- [`docs/methodology.md`](docs/methodology.md): the method overview for tasks, traces, scores, and case cards.
- [`docs/metrics.md`](docs/metrics.md): formal metric definitions and score semantics.
- [`docs/tasks.md`](docs/tasks.md): benchmark task families engineered to trigger looping, hallucinated fixes, and permission walls.
- [`docs/scoring-policy.md`](docs/scoring-policy.md): what is computed, proxied, or judged in public scores.
- [`docs/trace-schema.md`](docs/trace-schema.md): the minimal run/event contract for traces and the future visualizer.
- [`docs/case-card-spec.md`](docs/case-card-spec.md): the structure that public case pages follow.
- [`docs/faq.md`](docs/faq.md): the quick explanation page for new readers.
- [`docs/whitepaper-index.md`](docs/whitepaper-index.md): the guided entry point into the longer argument.
- [`whitepaper.md`](whitepaper.md): the architectural argument behind DEOA and ACC-style conflict monitoring.
- [`examples/stall-of-the-day/`](examples/stall-of-the-day/): public case index and founding cases.
- [`visualizer/`](visualizer/): trajectory visualization contract for loop clusters and pivot turns.
- [`benchmarks/`](benchmarks/): task-pack index plus the first minimal `permission-wall` pack.

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
