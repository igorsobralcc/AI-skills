---
name: distributed-systems-reliability
description: Design reliability for real remote dependencies using deadlines, selective retries, idempotency, circuit breaking, load shedding, consistency, and degraded modes.
---

# Distributed Systems Reliability

Use only when the refined architecture contains network boundaries.

## Golden rules

- Every remote call can delay, fail, duplicate, or return an ambiguous result. Propagate deadlines, cancellation, correlation, and budgets.
- Retry only transient, safe operations with bounded attempts, jitter, and idempotency.
- Define consistency, duplicate handling, failover, degraded behavior, and reconciliation explicitly.
- Observe dependency latency, saturation, failures, and recovery.

## Guardrails

- Avoid retry amplification, cascading timeouts, hidden fallbacks that corrupt state, unbounded queues, and unsupported availability claims.
- Do not distribute a cohesive transaction without accepting and documenting the consistency cost.
- Resilience libraries do not replace workload-specific failure design.
