---
name: database-schema-migrations
description: Plan and review code-first schema migrations, data backfills, compatibility windows, validation, sequencing, and recovery without automatically applying production changes.
---

# Database Schema Migrations

## Golden rules

- Code models, mappings, and version-controlled migrations manage schema evolution; generated operations and SQL still require database review.
- Prefer expand, deploy compatible code, backfill in bounded batches, validate, enforce, then contract.
- State supported source versions, lock behavior, transaction boundaries, replication impact, runtime compatibility, rollback or forward-recovery path, and verification.
- Keep the migration with the model change that requires it and test from a realistic prior schema.

## Guardrails

- Never auto-apply production migrations, assume down scripts restore lost data, or hide destructive operations behind ORM abstractions.
- Stop on unexplained drops, table rewrites, long locks, unbounded updates, provider differences, or missing backups and approval.
- Separate online application deployment from long-running data movement when risk requires it.
