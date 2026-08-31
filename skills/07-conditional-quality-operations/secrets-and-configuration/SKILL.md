---
name: secrets-and-configuration
description: Design configuration ownership, validation, environment separation, secret injection, rotation, and safe local development whenever settings or credentials are introduced.
---

# Secrets and Configuration

## Golden rules

- Classify each setting as public configuration, sensitive configuration, or secret and define its source, owner, validation, default, and lifecycle.
- Required production settings fail startup with safe diagnostics. Development fallbacks are explicit and unavailable in production.
- Prefer short-lived workload identity and managed secret delivery over static shared credentials.
- Design rotation so old and new credentials can overlap when consumers require it.

## Guardrails

- Never store secrets in source, images, examples, logs, command lines, test snapshots, or generated artifacts.
- Do not retrieve, reveal, create, rotate, or revoke real secrets without explicit authorization.
- Redact diagnostic output and avoid shared credentials or insecure defaults.
