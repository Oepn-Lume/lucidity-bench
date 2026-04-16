# Lucidity Visualizer

Lucidity-Visualizer is the planned trajectory view for benchmark traces.

## Goal

Turn retry-heavy logs into pictures that make looping obvious at a glance.

## First Output Spec

The first visual output should show:

- repeated local retries as dense red knots,
- successful architectural pivots as sharp green turns,
- the estimated cost burn attached to each loop cluster,
- the final path length versus essential path length.

## Minimal Data Contract

The visualizer should eventually accept a JSON trace with:

- step index,
- event type,
- failure family,
- similarity-to-previous-failure,
- estimated cost,
- pivot marker,
- solution marker.

That is enough to render a basic loop-vs-breakout picture even before a full UI exists.
