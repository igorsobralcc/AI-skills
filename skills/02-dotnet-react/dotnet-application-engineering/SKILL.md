---
name: dotnet-application-engineering
description: Implement or review modern .NET and C# applications with personal organization, analyzer, async, configuration, logging, testing, and build standards.
---

# .NET Application Engineering

Read `development-standards` and its .NET reference before implementation.

## Golden rules

- Organize by feature or capability under `src`, with behavioral tests under `tests`; keep infrastructure behind explicit boundaries.
- Use one class, interface, enum, struct, record, or delegate per matching file.
- Enable nullable reference types, .NET analyzers, repository code style, and warnings as errors. Prefer a root `.editorconfig` and analyzer-clean Release builds.
- Use constructor injection, validated options, structured logging, explicit errors, and cancellation across asynchronous boundaries.
- Choose unit, integration, contract, and acceptance tests by risk and meet the feature coverage target.

## Guardrails

- Preserve the supported target framework and existing compatible conventions.
- Avoid service locators, sync-over-async, swallowed cancellation, global mutable state, broad analyzer suppression, and speculative layers.
- Do not add ASP.NET, EF Core, or new packages unless the requested work requires them.
