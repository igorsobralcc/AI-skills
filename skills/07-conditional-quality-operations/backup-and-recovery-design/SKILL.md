---
name: backup-and-recovery-design
description: Define backup, restore, RPO, RTO, retention, encryption, isolation, dependency ordering, and recovery exercises when durable state is introduced or changed.
---

# Backup and Recovery Design

Activate when a project owns durable or business-critical state.

## Golden rules

- Derive recovery point and time objectives from business impact, then define protected data, configuration, keys, dependencies, frequency, retention, and ownership.
- Keep recoverable copies isolated from primary credentials and failure domains.
- Test restoration and application consistency, not merely backup job success.
- Document recovery ordering, validation, failback, communication, and exercise cadence.

## Guardrails

- Never expose backup credentials or sensitive content, initiate a live restore, or run a destructive exercise without authorization.
- Account for logs, files, object storage, schemas, secrets, and encryption keys—not only the primary database.
- Do not claim recoverability without restore evidence.
