---
name: secure-code-review
description: Review code for trust-boundary, authorization, injection, secret, cryptography, sensitive-data, tenant-isolation, and dependency risks when security-relevant behavior changes.
---

# Secure Code Review

Activate for exposed APIs, authentication, authorization, file or user input, sensitive data, administrative operations, multi-tenancy, or security-relevant dependencies.

## Golden rules

- Trace untrusted data from entry to validation, authorization, storage, rendering, logging, and sensitive sinks.
- Check authorization for the actual resource and action, not only authentication or endpoint role labels.
- Prefer platform cryptography and parameterized APIs; minimize stored, returned, and logged data.
- Report findings with credible failure paths, impact, affected boundary, and proportionate remediation.

## Guardrails

- Do not claim compliance, conduct active exploitation, reveal secrets, or provide unnecessary weaponized detail.
- Distinguish confirmed defects, likely risks, and hardening suggestions.
- Review does not authorize implementing fixes or probing external systems.
