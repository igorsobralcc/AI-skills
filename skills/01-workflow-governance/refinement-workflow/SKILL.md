---
name: refinement-workflow
description: Coordinate end-to-end refinement for a feature, bug, major change, or new project and finish with an actionable version-controlled specification.
---

# Refinement Workflow

Use this as the coordinator. Start with focused questions that establish the feature's intended outcome, boundaries, constraints, and material unknowns. Load only the domain, conditional, and opt-in skills whose triggers credibly apply.

## Question-led discovery

- Ask the user the smallest useful set of questions before settling consequential product, scope, architecture, security, delivery, or operational decisions. Prefer questions that resolve an ambiguity with a different outcome or trade-off.
- Establish the intended actor and outcome, success and failure behavior, scope and non-goals, affected systems or data, constraints, and acceptance evidence. Use the answers to refine acceptance criteria; do not turn unconfirmed assumptions into requirements.
- Review available skills whose names or descriptions plausibly match the work. For each applicable opt-in skill, ask whether it should be used, unless a repository policy or an already accepted decision answers it.
- Record each considered opt-in skill as `selected`, `not applicable`, or `deferred`, with a brief rationale. Record the choice in the specification; create a decision record when it establishes a durable project policy.
- Do not ask a generic questionnaire or enumerate every available skill. Questions are required only where the answer could materially change the refinement or implementation.

## Required sequence

1. Use `repository-onboarding` to establish current context.
2. Use `acceptance-criteria-design` to define outcomes, boundaries, and non-goals.
3. Select architecture, API, database, security, operational, delivery, .NET, and React skills according to scope. Resolve applicable opt-in skills before treating their rules as project policy.
4. Use `testing-strategy` after boundaries stabilize; map tests and the default 90% feature-specific line coverage target.
5. Use `technical-documentation` to define documentation impact and required artifacts.
6. Record every adopted consequential decision with `decision-record-management`; use `architecture-decision-records` for durable architectural choices.
7. Use `change-planning` last to create the specification file.

## Completion gate

The specification must be understandable without reconstructing the conversation and include scope, non-goals, acceptance criteria, architecture, contracts, data and migrations, tests and coverage, security, operations, documentation, selected or declined opt-in skills with rationale, decision links, implementation stages, and verification.

## Guardrails

- Refinement does not implement the feature.
- Do not load every skill defensively or design hypothetical future scale.
- Stop for user direction when an unresolved choice materially changes scope, architecture, data, security, compatibility, cost, or external systems.
