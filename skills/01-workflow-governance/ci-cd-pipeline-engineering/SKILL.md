---
name: ci-cd-pipeline-engineering
description: Design or review CI/CD pipelines that enforce repository standards, feature coverage, reproducible artifacts, least privilege, and safe promotion.
---

# CI/CD Pipeline Engineering

Enforce the specification's applicable quality gates automatically.

## Golden rules

- Run restore or install, format check, lint and static analysis, compile or type-check, tests, feature coverage, contract and migration validation, and production build as applicable.
- Make local verification and CI behavior agree. Build once and promote immutable artifacts.
- Pin executable automation dependencies and use least-privilege job permissions.
- Fail when the default 90% feature-specific coverage target or a higher specified target is not met.

## Guardrails

- Never expose secrets, run untrusted pull-request code with privileged credentials, hide failed checks, or publish mutable production artifacts.
- Do not deploy, change branch protection, or mutate external CI configuration without explicit authorization.
- Cache only reproducible outputs with complete keys.
