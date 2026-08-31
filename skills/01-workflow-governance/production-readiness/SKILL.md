---
name: production-readiness
description: Assess whether a change or service has sufficient security, configuration, health, observability, capacity, recovery, rollout, and ownership evidence for production.
---

# Production Readiness

Evaluate readiness against the approved specification and actual implementation.

## Golden rules

- Verify configuration validation, secret handling, dependency failure behavior, health and readiness, telemetry, capacity assumptions, data recovery, rollout, rollback, and operational ownership.
- Readiness differs from liveness; every critical dependency has bounded failure behavior.
- Release criteria are observable and measurable. Record missing evidence and residual risk.

## Conditional routing

Use `observability-engineering`, `secrets-and-configuration`, `backup-and-recovery-design`, `secure-code-review`, and `performance-engineering` when their triggers apply.

## Guardrails

- Do not certify a system as risk-free, deploy it, or accept residual risk for stakeholders.
- Block a readiness claim when critical controls or verification evidence are absent.
