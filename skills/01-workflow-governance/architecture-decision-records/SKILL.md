---
name: architecture-decision-records
description: Create and maintain ADRs for durable decisions about architecture, boundaries, patterns, data ownership, infrastructure, or major technical direction.
---

# Architecture Decision Records

Use ADRs for decisions whose consequences outlive one implementation task.

## Golden rules

- Use one architectural decision per record and a stable `ADR-NNN` identifier.
- Describe context and forces, credible alternatives, the decision, rationale, positive and negative consequences, and status.
- Record why the selected architecture is proportional to scope and why it avoids under- and over-engineering.
- Link the owning specification and any prior ADR being superseded.

## Guardrails

- Do not use ADRs for routine code choices or rewrite historical records after acceptance.
- Mark proposals honestly and never imply stakeholder approval that did not occur.
- Preserve rejected alternatives that materially explain the decision.
