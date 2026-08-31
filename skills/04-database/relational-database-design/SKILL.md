---
name: relational-database-design
description: Design relational schemas from domain invariants and access patterns before code-first ORM mapping, including keys, constraints, normalization, transactions, and indexes.
---

# Relational Database Design

## Golden rules

- Start with entities, invariants, ownership, lifecycle, access paths, cardinality, consistency, retention, and concurrency.
- Use stable keys, intentional nullability, foreign keys, uniqueness, checks, precision, and deletion behavior to protect data.
- Normalize by default and denormalize only for a measured access or reliability need with a reconciliation owner.
- Design indexes from real query shapes, selectivity, ordering, and write cost.
- Translate the approved model into code-first mappings and migrations without making the object model the sole design authority.

## Guardrails

- Avoid polymorphic foreign keys, comma-separated relationships, unbounded JSON as an escape from modeling, redundant indexes, and application-only invariants.
- Classify sensitive data and define retention before persistence.
- Do not create or mutate a live database without explicit authorization.
