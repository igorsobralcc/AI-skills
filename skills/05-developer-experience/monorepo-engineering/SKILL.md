---
name: monorepo-engineering
description: Design or review monorepo ownership, workspace boundaries, dependency policy, shared tooling, builds, tests, versioning, and releases when a monorepo is justified.
---

# Monorepo Engineering

## Golden rules

- Establish explicit package and capability ownership, public entry points, an acyclic dependency graph, and enforceable boundaries.
- Centralize truly shared tool configuration while allowing justified package differences.
- Define affected-build logic, cache inputs, versioning, and release relationships from actual ownership.
- Keep sharing intentional; duplication can be cheaper than coupling unrelated products.

## Guardrails

- Do not create a monorepo merely to share a utility or hide organizational dependencies.
- Avoid deep internal imports, circular ownership, universal rebuilds, global version coupling, and caches with incomplete keys.
- Preserve a full-verification escape path for dependency-graph uncertainty.
