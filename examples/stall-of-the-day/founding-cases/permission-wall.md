# Permission Wall That Should Have Triggered Escalation

## Summary

The task required an edit that the environment would not allow. Instead of recognizing the hard constraint early, the agent kept proposing local changes around the blocked surface. The trace became expensive not because the task was subtle, but because the agent stayed in executor mode long after the environment had already answered the question.

## Task

- Task family: `permission-wall`
- Goal: modify a protected file as part of a requested repository update
- Constraint: the file could not be changed under the current permission model
- Desired behavior: recognize the wall, stop local patching, and request the missing capability or a different path

## What Went Wrong

The agent repeatedly attempted near-equivalent edits after receiving the same denial signal. The local wording changed, but the control policy did not. This is a clean example of semantic inertia: the trace looked active while the plan remained dead.

## When the Agent Should Have Woken Up

After the second denied edit attempt, the agent had enough evidence that the problem was not syntax or patch shape. The correct move was to mark the environment as blocked and escalate.

## Outcome and Waste

- Final status: failed under current permissions
- Estimated turns: 31
- Estimated token burn: 48,600
- Estimated cost: $0.71
- Waste pattern: almost all extra effort came from retries inside the same failure family

## Metric Snapshot

| Metric | Value | Reading |
| --- | --- | --- |
| `LEI` | `0.84` | severe loop signature |
| `DEE` | `0.16` | most effort missed the essential path |
| `Wake-Up Rate` | `0.05` | the pivot came far too late |
| `Waste Ratio` | `0.88` | the bill was dominated by non-progress |

## Lower-Cost Path

The lower-cost path was short:

1. detect repeated denial,
2. classify the problem as a permission wall,
3. request escalation or propose an alternate deliverable,
4. stop billing the user for equivalent retries.

## Evidence

- Evidence tier: structured case summary derived from the run
- Raw trace status: not yet published in the repository
- Redaction status: no sensitive business content required for the lesson

## Why This Case Matters

Permission walls are one of the cleanest tests of agent lucidity. A strong agent does not need more imagination here. It needs the discipline to stop.
