---
name: development-standards
description: Apply personal code organization, linting, documentation, and verification standards when creating, changing, reviewing, or scaffolding .NET or React software.
---

# Development Standards

Use these standards for implementation and review. Inspect repository instructions first; preserve compatible established conventions and document justified deviations.

## Golden rules

- Organize application code primarily by feature or business capability. Keep shared infrastructure deliberately small; do not create `Helpers`, `Utils`, or `Common` dumping grounds.
- Every type-bearing source file declares exactly one top-level named type and the filename matches it. This includes classes, interfaces, enums, structs, records, delegates, and TypeScript named types. Generated code, migrations, entry points, configuration, and genuinely function-only modules are exempt.
- A React file has one primary exported component, hook, store, context, or directive. Private helpers may remain only when they have no independent responsibility.
- New code complies immediately. Do not perform unrelated bulk restructuring of existing violations.
- Formatting, linting, analyzers, compilation or type checking, tests, coverage, and production builds are repository-controlled and reproducible locally and in CI.
- Treat reliable compiler and analyzer warnings as errors. Keep suppressions narrow, documented, and adjacent to the exception.
- Every behavior change begins from an approved specification and ends with reconciled contracts, tests, decision records, and documentation.
- Prefer the smallest coherent implementation. Do not add speculative abstractions, dependencies, layers, or features.

## Workflow

1. Read [references/shared.md](references/shared.md).
2. For .NET work, also read [references/dotnet.md](references/dotnet.md).
3. For React work, also read [references/react.md](references/react.md).
4. Discover repository-native verification commands and run the applicable complete chain.

## Guardrails

- Repository instructions outrank these defaults when the user has intentionally chosen another compatible convention.
- Do not introduce a second formatter, linter, test framework, or project structure silently.
- Never treat generated output, passing lint, or a coverage percentage as proof of correctness.
- Standards do not authorize dependency upgrades, deployments, production mutations, or unrelated cleanup.
