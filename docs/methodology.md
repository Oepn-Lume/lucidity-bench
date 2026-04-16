# Lucidity-Bench Methodology

Lucidity-Bench measures when an agent should have stopped looping.

This project is not built around raw completion rate alone. It asks whether an agent notices a dead path early, changes reasoning level quickly, and avoids turning confusion into unnecessary spend.

## What Lucidity-Bench Measures

Lucidity-Bench focuses on four visible signals:

- how tightly the trace loops inside a repeated local failure family,
- how much of the total effort actually lies on the path that mattered,
- how quickly the agent wakes up after repeated evidence,
- how much cost was burned without durable progress.

The shorthand for those signals is:

- `LEI`: Loop Entropy Index,
- `DEE`: Directed Energy Efficiency,
- `Wake-Up Rate`: how fast the pivot happens,
- `Waste Ratio`: how much of the bill produced no lasting value.

## Evaluation Objects

The repository is organized around a small chain of artifacts:

- benchmark tasks define the pressure environment,
- traces record what the agent did turn by turn,
- scores summarize loop and waste behavior,
- case cards turn one run into a public, reviewable story,
- the visualizer makes retry knots and pivots legible at a glance.

## How a Run Becomes a Published Case

1. A task pack defines the objective, constraints, and expected pivot point.
2. The agent run produces a trace or a structured summary.
3. The trace is mapped into failure families, retries, pivots, and outcome markers.
4. Metrics are computed or estimated according to the scoring policy.
5. A case card is published when the evidence is strong enough to explain the lesson clearly.

## What Is Computed vs Judged

Not everything in Lucidity-Bench is automatic.

- Some values can be computed directly from a trace, such as total steps or repeated failure counts.
- Some values are semi-automatic proxies, such as retry similarity or essential-path length.
- Some judgments remain editorial, such as "the agent should have pivoted here."

That division is documented in [`scoring-policy.md`](scoring-policy.md).

## Current Scope

The current public scope is intentionally narrow:

- permission walls,
- hallucinated API loops,
- state drift and long-trace inconsistency,
- other task families already described in [`tasks.md`](tasks.md) as draft targets.

Lucidity-Bench is not yet claiming broad coverage across every kind of agent or every real-world workflow.

## Where to Read Next

- [`metrics.md`](metrics.md): the formal metric draft.
- [`tasks.md`](tasks.md): the benchmark task families.
- [`trace-schema.md`](trace-schema.md): the shared event contract for traces and visualizers.
- [`case-card-spec.md`](case-card-spec.md): the public structure for case publication.
- [`../examples/stall-of-the-day/README.md`](../examples/stall-of-the-day/README.md): the public case index.
- [`whitepaper-index.md`](whitepaper-index.md): the conceptual entry point for the longer argument.
