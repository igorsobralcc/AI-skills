---
name: sql-query-review
description: Review SQL and ORM-generated queries for correctness, security, cardinality, plans, null semantics, locking, bounds, and maintainability.
---

# SQL Query Review

## Golden rules

- Verify business semantics, join cardinality, null behavior, deterministic ordering, pagination, transaction context, and result bounds.
- Parameterize untrusted values and select only needed data.
- Inspect representative execution plans and data distributions for sensitive or hot queries; account for write and index costs.
- Review ORM query shape and emitted SQL, not only application syntax.

## Guardrails

- Reject injection paths, accidental cross joins, unbounded scans or writes, non-sargable hot predicates, and update or delete statements without a proven scope.
- Do not optimize from syntax alone or change behavior for speed.
- Production query execution and index changes require explicit authorization.
