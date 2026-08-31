---
name: scaffolding-and-code-generation
description: Create or review generators and templates that produce compliant project or feature structure without speculative layers or unsafe overwrites.
---

# Scaffolding and Code Generation

## Golden rules

- Generate the smallest useful structure that follows `development-standards`, including one type per file, lint configuration, tests, and verification hooks where applicable.
- Make generated ownership obvious and reruns deterministic.
- Validate names, paths, collisions, and template variables; preview changes before overwriting.
- Test that generated output restores, lints, builds, and runs its intended tests.

## Guardrails

- Do not create empty architecture layers, copy stale dependencies, overwrite maintained code silently, or generate secrets.
- Pin generator inputs and versions when reproducibility matters.
- Prefer language features and small templates over complex generation machinery.
