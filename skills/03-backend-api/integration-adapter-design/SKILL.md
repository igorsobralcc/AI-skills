---
name: integration-adapter-design
description: Design explicit adapters for external APIs, messaging, storage, identity, files, and vendors while preserving domain language and failure semantics.
---

# Integration Adapter Design

## Golden rules

- Translate provider models, identifiers, errors, and lifecycle at the boundary; keep domain behavior provider-neutral where it creates real substitution or test value.
- Define timeouts, cancellation, authentication, idempotency, retry classification, rate limits, pagination, and partial failures.
- Contract-test critical adapters and provide realistic fakes only at the adapter boundary.
- Preserve provider-specific semantics in documentation rather than pretending all vendors are interchangeable.

## Guardrails

- Do not wrap every library automatically, leak provider identifiers into public contracts, retry unsafe calls blindly, or swallow partial failure.
- Never log credentials or unredacted sensitive payloads.
- Do not contact or configure a real external service without authorization.
