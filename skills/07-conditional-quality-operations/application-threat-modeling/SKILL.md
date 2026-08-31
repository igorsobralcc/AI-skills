---
name: application-threat-modeling
description: Model assets, actors, trust boundaries, abuse cases, threats, controls, and residual risk for new exposed systems or consequential security boundaries.
---

# Application Threat Modeling

Activate for new externally accessible projects, authentication, sensitive data, multi-tenancy, file uploads, administrative workflows, or new trust boundaries.

## Golden rules

- Identify valuable assets, credible actors, entry points, data flows, trust boundaries, privileges, and abuse cases.
- Prioritize threats by impact and feasibility; map each accepted threat to preventive, detective, or recovery controls and verification.
- Record owners, residual risk, assumptions, and decisions in the specification.
- Revisit the model when boundaries, data, or capabilities change.

## Guardrails

- Do not generate exhaustive theoretical lists detached from architecture or accept risk for stakeholders.
- Protect sensitive diagrams and operational details.
- Distinguish planned controls from verified controls and mitigations from guarantees.
