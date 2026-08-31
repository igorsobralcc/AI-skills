---
name: refinement-workflow
description: Coordinate end-to-end refinement for a feature, bug, major change, or new project and finish with an actionable version-controlled specification.
---

# Refinement Workflow

Use this as the coordinator. Load only the domain and conditional skills whose triggers apply.

## Required sequence

1. Use `repository-onboarding` to establish current context.
2. Use `acceptance-criteria-design` to define outcomes, boundaries, and non-goals.
3. Select architecture, API, database, security, operational, .NET, and React skills according to scope.
4. Use `testing-strategy` after boundaries stabilize; map tests and the default 90% feature-specific line coverage target.
5. Use `technical-documentation` to define documentation impact and required artifacts.
6. Record every adopted consequential decision with `decision-record-management`; use `architecture-decision-records` for durable architectural choices.
7. Use `change-planning` last to create the specification file.

## Completion gate

The specification must be understandable without reconstructing the conversation and include scope, non-goals, acceptance criteria, architecture, contracts, data and migrations, tests and coverage, security, operations, documentation, decision links, implementation stages, and verification.

## Guardrails

- Refinement does not implement the feature.
- Do not load every skill defensively or design hypothetical future scale.
- Stop for user direction when an unresolved choice materially changes scope, architecture, data, security, compatibility, cost, or external systems.
