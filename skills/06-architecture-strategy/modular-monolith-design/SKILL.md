---
name: modular-monolith-design
description: Design a single deployable with enforceable business modules, explicit contracts, data ownership, dependency direction, and extraction-ready seams.
---

# Modular Monolith Design

## Golden rules

- Modules own cohesive capabilities and their data access. Dependencies cross explicit published contracts and remain acyclic.
- Keep in-process interaction simple while preserving transaction and consistency advantages.
- Enforce boundaries through project structure, visibility, tests, analyzers, or build rules appropriate to the stack.
- Extract a service only when independent deployment or operational ownership justifies distributed cost.

## Guardrails

- Do not simulate network transports internally, create shared-domain dumping grounds, or permit unrestricted cross-module database access.
- Avoid a project per trivial type and ceremonial layers without boundary value.
- Record exceptions and their removal or ownership plan.
