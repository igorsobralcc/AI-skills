---
name: specification-lifecycle
description: Maintain a specification through Draft, Approved, Implemented, Superseded, or Rejected states while keeping code, tests, contracts, decisions, and documentation reconciled.
---

# Specification Lifecycle

Treat the specification as the behavioral source of truth for the change.

## Golden rules

- Use explicit states: Draft, Approved, Implemented, Superseded, or Rejected.
- Reopen and reapprove a specification when a material behavioral, architectural, data, security, testing, or operational decision changes.
- Link acceptance evidence, migrations, contracts, documentation, and decision records.
- Mark Implemented only after the required verification evidence exists.

## Guardrails

- Never rewrite approved history to conceal changed decisions; record the change and its reason.
- Do not mark partial delivery complete.
- Keep abandoned and superseded specifications discoverable with clear successors.
