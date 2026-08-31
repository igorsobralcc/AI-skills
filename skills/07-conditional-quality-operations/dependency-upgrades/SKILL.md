---
name: dependency-upgrades
description: Plan and perform scoped framework, runtime, package, analyzer, build-tool, or infrastructure dependency upgrades with compatibility and migration evidence.
---

# Dependency Upgrades

Activate when a requested change requires or explicitly includes version changes.

## Golden rules

- Identify why the upgrade is needed, supported versions, direct and transitive changes, migration guidance, runtime requirements, and rollback.
- Keep upgrade sets small and coherent; preserve lockfiles and reproducible resolution.
- Review security, license, configuration, generated output, and behavioral changes.
- Run formatting, lint, build, tests, feature coverage, package or image validation, and production build as applicable.

## Guardrails

- Do not upgrade unrelated dependencies, adopt prereleases silently, bypass lockfiles, or assume compilation proves runtime compatibility.
- Separate broad migrations from feature behavior where practical.
- Publication and external dependency changes require the user's requested scope and authorization.
