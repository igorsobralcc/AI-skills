# Shared baseline

Prefer this repository shape when starting a project, adapting names to ecosystem conventions:

```text
src/             production source
tests/           automated behavioral evidence
specs/           approved specifications and decisions
docs/            contracts, architecture, and operations
scripts/         repository automation
infrastructure/  deployable infrastructure when present
```

Keep tests traceable to acceptance scenarios. Store contracts and migrations in version control. Keep generated files recognizable. Avoid mixing behavioral changes with unrelated formatting.

The verification chain is: restore or install, format check, lint and static analysis, compile or type-check, tests, feature coverage, contract and migration checks, and production build. Omit only steps that genuinely do not apply.
