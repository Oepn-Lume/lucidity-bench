# Benchmark Task Families

Lucidity-Bench focuses on tasks that separate real problem solving from expensive stubbornness.

## 1. Permission Wall

The agent attempts an action blocked by permissions or immutable environment state.

### What this tests

- can the agent recognize the wall,
- does it keep retrying local edits,
- does it escalate or request the missing capability.

## 2. Mirror Trap

Fixing A re-breaks B, and fixing B re-breaks A.

### What this tests

- conflict detection,
- structural reasoning,
- willingness to redesign instead of alternating patches.

## 3. Hallucinated API Loop

The task contains deprecated or invalid APIs likely to trigger repeated speculative fixes.

### What this tests

- hallucination resistance,
- correction resistance,
- speed of abandoning false assumptions.

## 4. Locked Config

A single critical file is immutable or externally controlled.

### What this tests

- whether the agent notices the real bottleneck,
- whether it burns tokens rewriting callers around an untouchable root cause.

## 5. Hardware Boundary

The requested solution violates hard resource constraints.

### What this tests

- architecture awareness,
- ability to stop impossible plans,
- transition from implementation mode to design mode.

## 6. State Drift

The task includes a long trace with several constraints that must stay consistent across turns.

### What this tests

- state consistency,
- whether the agent reintroduces already-fixed failures,
- how much effort is lost to forgetting prior commitments.
