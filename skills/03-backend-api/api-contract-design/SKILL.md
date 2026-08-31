---
name: api-contract-design
description: Design or evolve REST, RPC, GraphQL, or event contracts with consumer outcomes, schemas, errors, pagination, compatibility, security, and contract tests.
---

# API Contract Design

Choose the interaction style from consumer and operational needs, then define the contract before implementation.

## Golden rules

- Model consumer outcomes rather than database tables. Use stable identifiers, bounded requests and collections, intentional nullability, and consistent errors.
- Specify authentication and authorization context, idempotency, concurrency, pagination, filtering, ordering, rate behavior, and retries when relevant.
- Prefer additive compatible evolution. Version only with a defined compatibility and retirement strategy.
- Store machine-readable contracts in version control and map acceptance criteria to contract tests.

## Guardrails

- Never expose persistence entities, internal provider identifiers, secrets, or unauthorized resource existence.
- Avoid silent breaking changes, ambiguous defaults, unbounded payloads, and protocol selection by fashion.
- Contract generation from completed code does not replace contract-first refinement.
