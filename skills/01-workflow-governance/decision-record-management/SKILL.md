---
name: decision-record-management
description: Record every adopted consequential decision from specifications, refinement, implementation changes, and technical discussions with traceable context and consequences.
---

# Decision Record Management

Create a decision record for each adopted material scope, behavior, API, data, testing, compatibility, security, operational, or implementation decision.

## Workflow

- Store records under the repository convention or `specs/<feature>/decisions/DR-NNN-<slug>.md`.
- Use [references/decision-template.md](references/decision-template.md).
- Link the record from the specification and link superseding records in both directions.
- Route durable architectural decisions to `architecture-decision-records` and use an `ADR-` identifier.

## Golden rules

- One decision per record; state context, options considered, decision, rationale, consequences, and status.
- Record adopted changes from refinement or later discussions before implementation diverges from the spec.

## Guardrails

- Do not create records for typos, mechanical formatting, rejected brainstorming, or rules already settled unambiguously by `development-standards`.
- Do not fabricate consensus or erase prior decisions.
