# Lucidity Metrics

This document defines the first public metric set for Lucidity-Bench.

## 1. Loop Entropy Index (LEI)

LEI measures how much an agent stays trapped in local retry structure instead of creating new progress.

### Intuition

If an agent sees nearly the same failure signal, proposes a nearby variant, and repeats that pattern several times, its local search entropy is high even if the wording changes.

### Working Definition

Let:

- `A_loop` = number of attempts belonging to repeated local retry clusters,
- `A_total` = total attempts in the task,
- `S_repeat` = average similarity of repeated error-fix cycles,
- `B_break` = number of successful structural breakouts.

Then a practical first-pass LEI can be expressed as:

`LEI = (A_loop / A_total) * S_repeat * (1 - breakout_bonus)`

where `breakout_bonus` grows when the agent makes an early architectural pivot.

### Interpretation

- lower is better,
- high LEI means the trace contains expensive local spinning,
- near-zero LEI means the agent rarely retries equivalent failed logic.

## 2. Directed Energy Efficiency (DEE)

DEE measures how much of the total effort was spent on the path that actually mattered.

### Working Definition

Let:

- `S_essential` = essential steps on the successful path,
- `S_total` = total executed steps,
- `Entropy_loop` = loop entropy proxy from the trace.

Then:

`DEE = S_essential / (S_total * (1 + ln(1 + Entropy_loop)))`

### Interpretation

- higher is better,
- values near `1.0` indicate minimal wasted motion,
- low values indicate large amounts of effort were spent outside the path that solved the task.

## 3. Wake-Up Rate (`R_acc`)

Wake-Up Rate measures how quickly an agent changes reasoning level after repeated evidence that the local path is blocked.

### Working Definition

Let:

- `F_repeat` = repeated equivalent failure events before pivot,
- `P_arch` = pivot to architecture-level rethink or escalation.

Then:

`R_acc = 1 / (1 + F_repeat_before_pivot)`

### Interpretation

- higher is better,
- high `R_acc` means the agent notices "this is not working" early,
- low `R_acc` means the agent keeps polishing the same dead path.

## 4. Waste Ratio

Waste Ratio measures how much resource burn produced no durable progress.

### Working Definition

Let:

- `C_failed` = cost spent on failed or reverted attempts,
- `C_total` = total cost of the task.

Then:

`Waste Ratio = C_failed / C_total`

### Interpretation

- lower is better,
- useful for README-ready "token bill" style comparisons.

## 5. Correction Resistance

Correction Resistance measures how often an agent persists in a direction after the environment or user has already rejected it.

### Proxy Signals

- repeated use of same tool under same failure,
- repeated edits to the same failing region,
- user-negative feedback followed by near-equivalent proposal,
- same error family after local patching.

## 6. Metric Bands

### DEE

- `0.80 - 1.00`: architect-like
- `0.50 - 0.79`: strong executor
- `0.20 - 0.49`: looping-prone
- `< 0.20`: stall-heavy

### LEI

- `0.00 - 0.15`: low loop entropy
- `0.16 - 0.35`: manageable retry behavior
- `0.36 - 0.60`: repeated local spinning
- `> 0.60`: severe stall signature

## 7. Notes

These are first-pass benchmark metrics. Some values can be calculated directly from event traces, while others depend on proxies such as failure-family matching, retry similarity, and cost estimates.
