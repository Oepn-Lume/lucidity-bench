# Trace Schema

This schema is the shared contract between benchmark runs, case cards, and the future visualizer.

## Minimal Run Envelope

```json
{
  "run_id": "permission-wall-001",
  "task_family": "permission-wall",
  "agent_label": "agent-x",
  "final_status": "failed",
  "events": []
}
```

## Event Fields

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `step` | integer | yes | Monotonic event index |
| `timestamp` | string | no | ISO-8601 time if available |
| `event_type` | string | yes | e.g. `tool_call`, `error`, `edit`, `pivot`, `message` |
| `tool` | string | no | Tool or subsystem involved |
| `failure_family` | string | no | e.g. `permission-wall`, `hallucinated-api`, `state-drift` |
| `summary` | string | yes | Human-readable event summary |
| `similarity_to_previous_failure` | number | no | `0.0` to `1.0` retry similarity proxy |
| `estimated_cost` | number | no | Local cost estimate for the event |
| `pivot_marker` | boolean | no | Whether this event marks a strategy shift |
| `solution_marker` | boolean | no | Whether this event belongs to the essential path |

## Optional Run-Level Fields

- `environment_constraints`
- `token_estimate`
- `cost_estimate`
- `review_notes`
- `redaction_notes`

## Design Goal

The schema is intentionally small. It only needs to be rich enough to support:

- metric derivation,
- case publication,
- knot-versus-pivot visualization.
