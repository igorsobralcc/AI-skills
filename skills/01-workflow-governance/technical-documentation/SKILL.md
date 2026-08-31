---
name: technical-documentation
description: Plan and produce the appropriate documentation for every change, including documentation impact during refinement and reconciliation after implementation.
---

# Technical Documentation

Every change requires documentation at the appropriate level, even when the result is an explicit “no external documentation change” entry in the specification.

## Golden rules

- During refinement, identify affected specifications, API contracts, architecture diagrams, developer guides, runbooks, configuration references, migration notes, and user-facing behavior.
- Update documentation in the same change as the behavior it describes.
- Prefer authoritative, executable examples and link rather than duplicate schemas or configuration.
- Record audience, owner, current versus planned state, and verification commands where useful.

## Guardrails

- Do not document imagined behavior, expose secrets, or create comments that restate obvious code.
- Validate commands, links, examples, and diagrams against the implemented system.
- Do not close a specification until required documentation is reconciled.
