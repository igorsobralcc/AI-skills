---
name: observability-engineering
description: Design logs, metrics, traces, health signals, dashboards, sampling, and retention for backend services, jobs, integrations, and critical workflows.
---

# Observability Engineering

Activate during refinement for production services, external dependencies, background work, or critical user journeys.

## Golden rules

- Observe user outcomes, application flows, dependencies, saturation, failures, and recovery rather than instrumenting everything.
- Use structured events, stable correlation and trace identifiers, meaningful units, and bounded-cardinality dimensions.
- Separate liveness, readiness, and diagnostic detail. Define actionable dashboards and alert inputs with owners.
- Document sampling, retention, privacy, cost, and expected diagnostic workflow.

## Guardrails

- Never log secrets, credentials, raw sensitive payloads, or uncontrolled personal data.
- Avoid high-cardinality labels, duplicate telemetry, misleading health, and alerts unsupported by reliable signals.
- Telemetry configuration in live systems requires authorization.
