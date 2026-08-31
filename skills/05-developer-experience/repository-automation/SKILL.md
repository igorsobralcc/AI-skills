---
name: repository-automation
description: Create or review deterministic repository scripts for build, validation, generation, maintenance, and policy with safe inputs and CI-compatible behavior.
---

# Repository Automation

## Golden rules

- Automate repeated, error-prone workflows with explicit inputs, outputs, exit codes, and useful failure messages.
- Provide a noninteractive CI mode and preserve local/CI parity.
- Validate paths and prerequisites; make repeated runs idempotent where practical.
- Test important policy validators and generators against positive and negative cases.

## Guardrails

- Default destructive operations to dry-run or require explicit confirmation and exact targets.
- Never print secrets, download mutable executables without integrity controls, or hide failures.
- Reuse existing task runners and scripts when they already own the workflow.
