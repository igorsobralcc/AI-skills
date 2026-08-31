---
name: backend-application-design
description: Define proportional backend architecture, capability boundaries, application flows, transactions, concurrency, failures, integrations, and persistence during refinement or implementation.
---

# Backend Application Design

Choose architecture from the approved scope, quality attributes, team, and credible evolution.

## Golden rules

- Organize by business capability; give invariants and data clear owners; place infrastructure behind explicit adapters.
- Define transaction, consistency, concurrency, failure, retry, and recovery behavior for each important flow.
- Prefer the simplest structure that protects current invariants and enables expected change. A modular monolith is the default comparison point for new backends.
- Record the selected pattern, rejected credible alternatives, and proportionality rationale.

## Guardrails

- Do not mandate DDD, clean architecture, CQRS, event sourcing, or microservices.
- Avoid generic repositories, speculative layers, distributed transactions, hidden shared state, and abstractions without a second real use.
- Do not under-engineer security, data integrity, failure handling, or operability to keep diagrams simple.
