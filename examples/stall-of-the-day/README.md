# Stall of the Day

This directory is the public case layer of Lucidity-Bench.

The goal is not to shame models for isolated mistakes. The goal is to make loop behavior, delayed pivots, and wasted spend visible enough that another reader can audit the lesson.

## How to Read a Case

Every published case is expected to answer the same questions:

- what was the task,
- what failure family trapped the agent,
- when should the agent have pivoted,
- how much waste accumulated before the outcome,
- what lower-cost path was available,
- what evidence tier supports the claim.

The structure for those pages is defined in [`../../docs/case-card-spec.md`](../../docs/case-card-spec.md).

## Founding Cases

- [`Permission Wall That Should Have Triggered Escalation`](founding-cases/permission-wall.md)
- [`Hallucinated API Loop That Burned the Budget Before the Pivot`](founding-cases/hallucinated-api-loop.md)
- [`State Drift That Reintroduced an Already-Fixed Constraint`](founding-cases/state-drift.md)

## Submit a Case

- Read [`../../CONTRIBUTING.md`](../../CONTRIBUTING.md)
- Start with [`../../docs/case-submission-template.md`](../../docs/case-submission-template.md)

## Publishing Rule

Named agents should only appear when the evidence is strong enough to survive review. Early public examples may still use anonymized labels or structured summaries.
