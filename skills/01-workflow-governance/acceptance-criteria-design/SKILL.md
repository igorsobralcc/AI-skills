---
name: acceptance-criteria-design
description: Turn product intent into concrete, testable outcomes and boundaries during feature, bug, or project refinement without prescribing unnecessary implementation details.
---

# Acceptance Criteria Design

Define observable behavior before architecture and implementation are finalized.

## Golden rules

- Describe actor, preconditions, action, observable outcome, and relevant persisted or emitted effects.
- Include unhappy paths, authorization, validation, concurrency, recovery, compatibility, and operational behavior when relevant.
- Make scope and non-goals explicit. Use concrete examples for ambiguous rules.
- Give each criterion a stable identifier so specifications, tests, and documentation can trace to it.

## Guardrails

- Do not invent product decisions or encode a preferred implementation as a requirement.
- Do not accept tautologies such as “works correctly.”
- Surface consequential ambiguity for resolution and record the adopted decision.
