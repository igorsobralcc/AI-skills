---
name: aspnet-api-design
description: Implement or review ASP.NET APIs from an approved contract, including endpoints, validation, errors, authentication boundaries, caching, concurrency, and integration tests.
---

# ASP.NET API Design

Use with `api-contract-design` and `dotnet-application-engineering` after refinement.

## Golden rules

- Define or update the version-controlled contract before endpoint implementation.
- Keep transport adapters thin; validate and bound input; return consistent problem details and intentional HTTP semantics.
- Propagate cancellation, correlation, and trace context. Keep authentication distinct from resource-level authorization.
- Design idempotency, conditional requests, caching, pagination, and compatibility when the use case requires them.
- Prove observable behavior with integration or contract tests using the real application pipeline.

## Guardrails

- Never log secrets or sensitive request bodies, leak private resource existence, trust client claims blindly, or expose persistence entities directly.
- Do not add versioning, filters, middleware, or abstractions without a demonstrated contract or cross-cutting need.
- Preserve `Program` testability and production startup validation.
