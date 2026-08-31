---
name: react-application-engineering
description: Implement or review React and TypeScript applications with feature organization, component boundaries, state ownership, hooks discipline, accessibility, testing, and production builds.
---

# React Application Engineering

Read `development-standards` and its React reference before implementation.

## Golden rules

- Organize components, hooks, schemas, services, tests, and styles by feature. Keep reusable primitives intentional.
- Use one primary exported component, hook, context, or store per file; put independent named types in matching files.
- Use strict TypeScript and runtime validation at external boundaries. Derive state instead of synchronizing duplicates.
- Use effects only for external synchronization. Design loading, empty, error, success, disabled, and retry states.
- Preserve semantic HTML, keyboard behavior, focus, responsive behavior, and accessible names.
- Verify type-aware linting, hooks and accessibility rules, formatting, tests, feature coverage, and production build.

## Guardrails

- Do not choose a meta-framework, state library, form library, or design system without repository context.
- Avoid stale closures, unstable keys, prop-state duplication, broad contexts, inaccessible custom controls, and premature memoization.
- Do not expose secrets or assume client-side validation or authorization is authoritative.
