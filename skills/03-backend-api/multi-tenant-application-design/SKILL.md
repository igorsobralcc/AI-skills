---
name: multi-tenant-application-design
description: Design tenant identity, isolation, authorization, data partitioning, configuration, quotas, migrations, observability, and operations when multi-tenancy is required.
---

# Multi-Tenant Application Design

## Golden rules

- Tenant context is established from trusted identity and remains explicit and immutable throughout an operation.
- Choose shared, partitioned, schema, database, or account isolation from security, compliance, scale, cost, and operations requirements.
- Enforce isolation at multiple layers, including authorization, data access, caches, jobs, files, telemetry, and rate limits.
- Define tenant-aware migrations, backup and restore, support access, and deletion.

## Guardrails

- Never rely on a client-supplied tenant filter alone, share tenant cache keys, expose cross-tenant metrics, or run unsafe global data operations.
- Do not add multi-tenancy speculatively.
- Record residual isolation risk and operational trade-offs.
