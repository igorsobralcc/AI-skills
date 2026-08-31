---
name: testing-strategy
description: Map risk-based tests during refinement after boundaries stabilize, with a default minimum of 90 percent line coverage for the specific feature.
---

# Testing Strategy

Create the test plan before implementation and reconcile it afterward.

## Golden rules

- Map each acceptance criterion to unit, integration, contract, component, end-to-end, migration, security, or performance evidence as appropriate.
- Target at least 90% line coverage for code owned or changed by the feature. Use changed-code or feature-scoped measurement rather than hiding gaps in a repository-wide average.
- A user may request a higher target. A percentage never replaces boundary, failure, concurrency, authorization, or regression scenarios.
- Tests must be deterministic, independently diagnosable, and organized around observable behavior.

## Guardrails

- Do not add tests merely to execute lines, assert implementation trivia, or mock away the behavior being proved.
- Exclude generated code and migrations only through explicit repository policy.
- If the feature boundary cannot be measured reliably, document the method and use the narrowest defensible proxy.
