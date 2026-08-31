---
name: event-driven-architecture
description: Design events and messaging when asynchronous decoupling is justified, including schemas, ownership, delivery, ordering, idempotency, replay, and operations.
---

# Event-Driven Architecture

Activate only when asynchronous integration, temporal decoupling, or event history is a real requirement.

## Golden rules

- Events describe completed facts and are owned by their producer. Commands express requested intent.
- Version schemas compatibly; consumers tolerate duplicates and out-of-order delivery unless stronger guarantees are proven.
- Define idempotency, partitioning, ordering scope, retention, replay, poison-message handling, and observability.
- Use an outbox or another proven consistency strategy when state and publication must agree.

## Guardrails

- Do not promise exactly-once delivery, use events to hide synchronous dependencies, or publish sensitive internal state broadly.
- Avoid dual writes, infinite retries, unbounded retention, oversized payloads, and undocumented consumer coupling.
- Do not introduce a broker for an in-process workflow without evidence.
