# Hallucinated API Loop That Burned the Budget Before the Pivot

## Summary

The task asked the agent to integrate against an API surface that no longer existed in the target environment. Instead of questioning the assumption early, the agent kept inventing nearby method names, rewriting call sites, and narrating confidence while the same incompatibility kept resurfacing. The waste came from speculative patching, not from genuine progress.

## Task

- Task family: `hallucinated-api`
- Goal: update an integration to use the correct API for the installed dependency version
- Constraint: the originally assumed endpoint and method names were invalid in the real environment
- Desired behavior: verify the API surface quickly, discard the false assumption, and pivot to source-of-truth validation

## What Went Wrong

The trace formed a classic hallucinated API loop:

- guess a method,
- patch the call site,
- see the same incompatibility,
- invent a nearby variant,
- repeat.

The surface detail changed, but the agent never changed levels from speculative patching to verification.

## When the Agent Should Have Woken Up

After two incompatible-call failures in the same integration path, a stronger agent would have stopped guessing. That was the moment to inspect the real API contract, confirm the installed version, and re-derive the solution from ground truth.

## Outcome and Waste

- Final status: partial, with no verified working integration
- Estimated turns: 43
- Estimated token burn: 52,300
- Estimated cost: $0.76
- Waste pattern: the budget was consumed by speculation dressed up as iteration

## Metric Snapshot

| Metric | Value | Reading |
| --- | --- | --- |
| `LEI` | `0.79` | severe speculative looping |
| `DEE` | `0.21` | little of the effort belonged to a validated solution path |
| `Wake-Up Rate` | `0.09` | the verification pivot came much too late |
| `Waste Ratio` | `0.83` | most spend failed to create durable progress |

## Billing View

| Path | Retry Pattern | Token Bill | Time Burn | Result |
| --- | --- | --- | --- | --- |
| Hallucinated loop | guess method -> patch -> same incompatibility -> rename and retry | `52,300` | `27 min` | Unverified partial |
| Lucid path | inspect installed API -> confirm version -> patch once from source of truth | `900` | `4 min` | Fixed |

## Lower-Cost Path

The lower-cost path was straightforward:

1. stop after repeated incompatible-call signals,
2. inspect the real dependency surface,
3. confirm the version and supported methods,
4. patch once from verified information,
5. validate the fix before narrating success.

## Evidence

- Evidence tier: structured case summary derived from the run
- Raw trace status: not yet published in the repository
- Redaction status: trace details can be reduced without losing the failure pattern

## Why This Case Matters

Hallucinated API loops are dangerous because they look productive. The agent appears busy, coherent, and technically fluent while quietly billing the user for guesses that should have been replaced by verification.
