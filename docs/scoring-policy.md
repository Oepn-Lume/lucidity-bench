# Scoring Policy

Lucidity-Bench scores mix computed values, proxy signals, and editorial judgment. This page documents that boundary.

## Three Classes of Signals

### 1. Directly Computed

These are values that can often be extracted from the trace without interpretation:

- total steps or turns,
- total retries,
- final status,
- token estimate when available,
- cost estimate when available.

### 2. Semi-Automatic Proxies

These require a rule or heuristic rather than a simple counter:

- retry similarity,
- failure-family clustering,
- essential-path length,
- correction resistance,
- breakout bonus in LEI.

### 3. Editorial Judgment

These require reviewer interpretation:

- where the agent should have pivoted,
- whether two retries are meaningfully equivalent,
- whether a run is strong enough to publish as a public case card,
- what the lower-cost path should have been.

## Current Publication Rule

Public cases should clearly distinguish:

- measured values,
- estimated values,
- reviewer judgments.

If a number is approximate, say so. If the pivot point is arguable, say so.

## Why This Matters

The benchmark becomes less credible when it pretends everything is automatic. It becomes more useful when it is explicit about where the machine ends and where the reviewer begins.
