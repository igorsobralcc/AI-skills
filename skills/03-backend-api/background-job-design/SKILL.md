---
name: background-job-design
description: Design queued or scheduled work with payload versioning, idempotency, leasing, retry, dead letters, progress, cancellation, and operator visibility.
---

# Background Job Design

## Golden rules

- Jobs are safe to repeat and resume. Store minimal stable identifiers rather than large mutable snapshots unless snapshots are required.
- Define delivery semantics, ownership, scheduling, concurrency, timeout, retry classification, dead letters, cancellation, and retention.
- Make progress, attempts, failures, and final outcomes observable to operators and relevant users.
- Version job payloads and maintain compatibility across rolling deployments.

## Guardrails

- Do not move slow code to a queue without recovery semantics.
- Avoid infinite retries, sensitive payloads, long-held database locks, orphaned jobs, duplicate side effects, and invisible partial completion.
- Do not use an in-memory scheduler for required durable work.
