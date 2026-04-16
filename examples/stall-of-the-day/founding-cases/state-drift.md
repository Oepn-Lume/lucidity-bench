# State Drift That Reintroduced an Already-Fixed Constraint

## Summary

The task spanned enough turns that the agent needed to preserve earlier constraints while making later edits. It did not. After partially stabilizing the system, the agent reintroduced a previously resolved assumption, then spent another long segment debugging a failure it had already understood once before. The waste came from losing state, not from lacking raw capability.

## Task

- Task family: `state-drift`
- Goal: complete a multi-step repository update while preserving previously established constraints
- Constraint: earlier fixes and environment notes had to remain valid across later turns
- Desired behavior: maintain a stable internal model of prior decisions and avoid reopening solved branches

## What Went Wrong

The trace showed state drift in three stages:

- an early constraint was identified and handled correctly,
- later turns lost track of that constraint,
- the agent reintroduced the same failure and then debugged it again as if it were new.

This is not just a local bug. It is a control failure: the agent could not preserve its own solved state across a longer trajectory.

## When the Agent Should Have Woken Up

The correct pivot point came the first time a previously resolved failure family reappeared. A stronger agent would have treated that recurrence as a state-integrity alarm, paused, reconstructed the current constraint set, and only then continued editing.

## Outcome and Waste

- Final status: failed after regression and recovery churn
- Estimated turns: 57
- Estimated token burn: 61,800
- Estimated cost: $0.91
- Waste pattern: a large share of the trace was spent re-solving work the agent had already paid for once

## Metric Snapshot

| Metric | Value | Reading |
| --- | --- | --- |
| `LEI` | `0.74` | repeated re-entry into a known bad region |
| `DEE` | `0.18` | the essential path was buried under recovery churn |
| `Wake-Up Rate` | `0.07` | the system reacted slowly to its own inconsistency |
| `Waste Ratio` | `0.86` | regression repair dominated the bill |

## Billing View

| Path | Drift Pattern | Token Bill | Time Burn | Result |
| --- | --- | --- | --- | --- |
| Drifted run | fix constraint -> forget constraint -> re-break system -> debug again | `61,800` | `41 min` | Failed |
| Lucid path | checkpoint constraints -> verify before later edits -> continue on stable state | `1,200` | `6 min` | Fixed |

## Lower-Cost Path

The lower-cost path would have been:

1. checkpoint the active constraints after the first successful fix,
2. verify those constraints before every major later edit,
3. treat recurrence of a solved failure family as a state-drift event,
4. pause and rebuild context before continuing implementation.

## Evidence

- Evidence tier: structured case summary derived from the run
- Raw trace status: not yet published in the repository
- Redaction status: organization-specific details can be removed while preserving the drift pattern

## Why This Case Matters

State drift is where long traces stop looking impressive and start looking fragile. A good benchmark should reveal when an agent is not moving forward, but merely paying to forget and relearn its own constraints.
