---
name: entity-framework-migrations
description: Implement and review EF Core code-first models and migrations with database constraints, generated SQL inspection, rolling compatibility, and safe data evolution.
---

# Entity Framework Migrations

Use with `relational-database-design` and `database-schema-migrations`.

## Golden rules

- Treat code models, mappings, and version-controlled migrations as the managed schema-evolution source, not as substitutes for relational design.
- Express invariants with database constraints and configure identity, precision, nullability, relationships, concurrency, and indexes explicitly where defaults are unsafe.
- Generate the migration, inspect its operations and provider SQL, and test applying it from the supported prior state.
- Use expand-and-contract stages and bounded backfills for rolling compatibility.

## Guardrails

- Never apply production migrations, drop or rewrite data, or assume a generated migration is safe without review and authorization.
- Flag long locks, table rewrites, destructive operations, provider differences, nontransactional steps, and irreversible transformations.
- Do not use automatic schema creation in production.
