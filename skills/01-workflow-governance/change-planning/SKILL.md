---
name: change-planning
description: Convert completed refinement into scoped implementation work and create the final version-controlled specification as the required output.
---

# Change Planning

Run after refinement decisions are sufficiently settled.

## Required output

Create `specs/<feature-name>/spec.md` or the repository's established equivalent using [references/spec-template.md](references/spec-template.md). Do not finish with only a chat plan.

## Golden rules

- Plan around observable outcomes and acceptance-criterion identifiers.
- Include affected components, contracts, data, migrations, dependencies, documentation, risks, compatibility, rollout, verification, and explicit non-goals.
- Break implementation into coherent stages that can be verified without implying permission to commit or deploy.
- Link all applicable decision records and preserve open questions clearly.

## Guardrails

- Do not silently resolve consequential open decisions while writing the spec.
- Do not expand scope with optional improvements.
- Mark the specification Draft until its required decisions are approved.
