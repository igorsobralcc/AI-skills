---
name: acceptance-criteria-design
description: Turn product intent into concrete, testable outcomes and boundaries during feature, bug, or project refinement without prescribing unnecessary implementation details.
---

# Acceptance Criteria Design

Define observable behavior before architecture and implementation are finalized.

## Discovery questions

- Ask focused questions when the intended actor, outcome, boundaries, business rules, failure behavior, or acceptance evidence remains unclear.
- Ask about relevant constraints and existing project policies only when they can change the observable behavior or scope.
- Turn answered questions into criteria, non-goals, or explicit open questions. Preserve unresolved consequential choices for the refinement coordinator; do not infer an answer to keep the process moving.

## Golden rules

- Describe actor, preconditions, action, observable outcome, and relevant persisted or emitted effects.
- Include unhappy paths, authorization, validation, concurrency, recovery, compatibility, and operational behavior when relevant.
- Make scope and non-goals explicit. Use concrete examples for ambiguous rules.
- Give each criterion a stable identifier so specifications, tests, and documentation can trace to it.
- Distinguish requirements from selected delivery or implementation policies, such as an opted-in branching workflow.

## Guardrails

- Do not invent product decisions or encode a preferred implementation as a requirement.
- Do not accept tautologies such as “works correctly.”
- Surface consequential ambiguity for resolution and record the adopted decision.
