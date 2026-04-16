# Beyond World Models: Toward Agents That Wake Up

## Thesis

The next leap in agent capability will not come from simulating more of the world in longer traces. It will come from learning when to stop simulating, when to detect structural conflict, and when to escalate from local repair to architectural rethink.

Lucidity-Bench exists to measure that shift.

## The Problem

Current coding agents often look capable because they can produce long, coherent traces. But long traces can hide three failure modes:

1. **Semantic inertia**: the agent keeps trying local edits after the environment has already shown the path is blocked.
2. **Looping under uncertainty**: the agent treats repeated failure as a reason to keep searching the same neighborhood.
3. **Cost blindness**: the system consumes large token budgets without recognizing that its search is no longer productive.

These are not just product issues. They are architectural issues.

## The DEOA Claim

DEOA (Dynamic Environment Operating Agent) is the proposed design stance behind Lucidity-Bench. It assumes that a high-quality agent should:

- prioritize strategy over endless simulation,
- monitor conflict between expectation and feedback,
- trip a circuit breaker when retry patterns become self-similar,
- escalate to a higher reasoning layer instead of polishing a blocked local path.

This is why Lucidity-Bench tracks not only whether the task was solved, but how quickly the agent woke up to the fact that its current plan was dead.

## ACC-Inspired Conflict Monitoring

An ACC-inspired agent architecture does not need to understand every detail of the world before acting. It needs to notice when repeated action is no longer informative.

In practical benchmark terms, this means:

- fewer repeated retries after equivalent errors,
- earlier detection of permission walls and invalid APIs,
- better separation between local bug-fixing and global path redesign,
- lower waste ratio under constrained environments.

## Why Loop Metrics Matter

The difference between a novice executor and an architectural agent is not just raw intelligence. It is the ability to break out of unproductive local search. Lucidity-Bench therefore treats looping behavior as a first-class signal, not as incidental noise.

## Relationship to Lume

Within a broader Lume-style system, Lucidity-Bench provides the measurement layer:

- LEI and DEE make looping and waste visible,
- benchmark tasks create comparable pressure,
- public case cards make failures legible to developers,
- DEOA provides the design target for what a better agent should look like.

## Working Hypothesis

An agent that consistently achieves high DEE and low LEI is not merely "more efficient." It is exhibiting a different control policy:

- earlier conflict recognition,
- lower correction resistance,
- higher state consistency,
- faster transition from executor mode to architect mode.

That is the hypothesis this repository is designed to test.
