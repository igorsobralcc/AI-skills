---
name: sdk-and-client-library-design
description: Design idiomatic SDKs and client libraries with stable APIs, authentication, timeouts, retries, pagination, errors, compatibility, tests, and releases.
---

# SDK and Client Library Design

## Golden rules

- Start from the versioned service contract and expose an idiomatic, minimal public surface for the target language.
- Make authentication, timeout, cancellation, pagination, rate behavior, retries, and errors explicit.
- Retry only safe transient operations; preserve server request identifiers and diagnostic context.
- Test against contract fixtures and representative consumer projects; document compatibility and migration.

## Guardrails

- Do not hide meaningful network semantics, log secrets, auto-page without bounds, or expose generated internals as stable APIs.
- Publishing and signing require explicit authorization.
- Generated code requires review for naming, compatibility, and one-type-per-file standards where applicable.
