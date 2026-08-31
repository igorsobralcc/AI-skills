---
name: code-review
description: Review an implementation against its specification, decisions, standards, contracts, migrations, tests, documentation, security, and operational requirements.
---

# Code Review

Lead with actionable findings ordered by impact and cite exact locations.

## Review gates

- Specification and acceptance-criterion conformance.
- Architecture and dependency boundaries, one-type-per-file, linting, and organization.
- API compatibility, authorization, persistence model, generated migration, and query behavior.
- Test completeness and feature-specific coverage target.
- Documentation and decision-record reconciliation.
- Production-readiness implications.

## Guardrails

- Do not rewrite for taste, duplicate automated lint output, or report speculative failures without a credible path.
- Distinguish blocking defects, risks, and optional suggestions.
- Review does not authorize implementing fixes or mutating external systems.
