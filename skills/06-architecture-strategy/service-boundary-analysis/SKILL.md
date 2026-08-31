---
name: service-boundary-analysis
description: Evaluate business capability, data ownership, transactions, change cadence, scaling, reliability, and team boundaries before choosing service seams.
---

# Service Boundary Analysis

## Golden rules

- Begin with cohesive business capabilities, authoritative data, invariants, and ownership rather than entities or technical layers.
- Quantify cross-boundary latency, consistency, failure, deployment, security, and operational costs.
- Compare a modular monolith with distributed alternatives and record why separation is necessary now.
- Define contracts, data ownership, migration stages, and team responsibility for every proposed boundary.

## Guardrails

- Do not split by database table, controller, or anticipated scale without evidence.
- Avoid shared-database services, chatty synchronous boundaries, distributed transactions, and cyclic ownership.
- Prefer the modular option when separation evidence is weak.
