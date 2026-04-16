# Contributing to Lucidity-Bench

Lucidity-Bench is still early, but it is already open to useful contributions. The fastest way to help is to improve the benchmark's evidence, not its rhetoric.

## Ways to Contribute

- submit a reproducible stall case,
- improve the wording or structure of benchmark docs,
- propose a benchmark task or task-pack refinement,
- improve the trace, scoring, or visualizer contracts,
- tighten methodology, caveats, or redaction guidance.

## Before You Submit

Please bring enough information for another reader to understand what happened without guessing:

- task goal and environment constraints,
- final status,
- the failure family involved,
- where the agent should have pivoted,
- approximate steps, turns, tokens, or cost,
- whether the trace is public, redacted, or private-review only.

If the case includes sensitive material, redact secrets and private identifiers, but preserve the failure chain.

## How to Submit a Case

Start with the template in [`docs/case-submission-template.md`](docs/case-submission-template.md).

Good case submissions usually include:

- a short title,
- the agent name or an anonymized label,
- a trace excerpt or structured summary,
- a metric snapshot or candidate values,
- one paragraph explaining why the case is structurally interesting.

## How to Propose a Doc or Benchmark Change

- open an issue with the problem statement and the proposed change,
- or open a PR with the wording update and any supporting rationale,
- keep changes narrow when possible so the repository stays reviewable.

## Review Standard

Submissions are favored when they are:

- reproducible or at least inspectable,
- honest about uncertainty,
- explicit about what was measured versus inferred,
- useful to benchmark builders beyond one brand or one model.

Submissions are usually rejected when they are:

- just a conclusion without evidence,
- mostly marketing language,
- impossible to review because the task or failure pattern is underspecified,
- framed as model takedowns instead of benchmark evidence.

## Communication

For benchmark collaboration, documentation questions, or case submission follow-up, contact `dspwatch@gmail.com`.
