# AI Skills

A curated catalog of reusable development skills for specification-driven
.NET, React, backend, API, and database work.

The collection turns development preferences into explicit workflows, golden
rules, and guardrails. Its purpose is not to prescribe maximum ceremony. It is
to make architecture, implementation, testing, documentation, and production
decisions deliberate, traceable, and proportional to the work.

## What this repository contains

- 53 individually usable skills.
- A coordinator that turns refinement into a version-controlled specification.
- Shared .NET and React organization and linting standards.
- Backend, API, database, developer-experience, and architecture guidance.
- Conditional security, reliability, performance, recovery, and debugging
  skills that activate only when their triggers apply.
- Reusable specification and decision-record templates.

Start with the [complete searchable catalog](skills/CATALOG.md).

## Core principles

### Specification-driven changes

Every behavior-changing feature, bug fix, or consequential refactor begins with
refinement and ends that phase with a version-controlled specification. The
specification records scope, non-goals, acceptance criteria, architecture,
contracts, data, tests, documentation, risks, decisions, and verification.

### Proportional architecture

Architecture is selected from current scope, quality attributes, team needs,
and credible evolution. Skills must actively guard against both speculative
over-engineering and unsafe under-engineering. A modular monolith is the
default comparison point for new backends, not an unconditional outcome.

### Traceable decisions

Every adopted consequential refinement or implementation decision receives a
decision record. Durable decisions about architecture, boundaries, data
ownership, infrastructure, or major technical direction receive an ADR.

### Tests mapped during refinement

Testing is designed after feature boundaries stabilize. Acceptance criteria
map to appropriate unit, integration, contract, component, end-to-end,
migration, security, or performance evidence. The default minimum is 90% line
coverage for code owned or changed by the feature; coverage never replaces
meaningful behavioral scenarios.

### Documentation is part of the change

Every change has a documentation impact, even when the result is an explicit
statement that no external documentation changes are required. Documentation
is planned during refinement and reconciled before the specification is marked
Implemented.

### Consistent code organization

- Organize code primarily by feature or business capability.
- Keep shared infrastructure small and intentional.
- Do not create generic `Helpers`, `Utils`, or `Common` dumping grounds.
- Every type-bearing source file declares exactly one top-level named type, and
  its filename matches the type.
- A React file contains one primary exported component, hook, context, store,
  or directive.
- Generated code, migrations, entry points, configuration, and genuinely
  function-only modules are exempt from the one-type rule.
- New code complies immediately; unrelated bulk restructuring is not required.

### Automated quality gates

Formatting, linting, static analysis, compilation or type checking, tests,
feature coverage, contracts, migrations, and production builds are
repository-controlled and reproducible locally and in CI. Reliable warnings
are treated as errors, and suppressions remain narrow and documented.

## Skill catalog

| Category | Count | Focus |
| --- | ---: | --- |
| [Workflow and governance](skills/01-workflow-governance) | 16 | Refinement, token efficiency, specifications, decisions, tests, documentation, review, CI, branching policy, readiness, skill discovery |
| [.NET and React](skills/02-dotnet-react) | 4 | .NET/C#, ASP.NET, EF Core, and React implementation |
| [Backend and API](skills/03-backend-api) | 9 | Application design, contracts, integration, reliability, identity, tenancy, caching |
| [Database engineering](skills/04-database) | 3 | Relational design, code-first migrations, and SQL review |
| [Developer experience](skills/05-developer-experience) | 6 | Local setup, automation, CLIs, generators, monorepos, and internal tooling |
| [Architecture and strategy](skills/06-architecture-strategy) | 7 | Boundaries, modularity, diagrams, debt, sourcing, platforms, and SDKs |
| [Conditional quality and operations](skills/07-conditional-quality-operations) | 8 | Security, observability, secrets, threats, recovery, performance, upgrades, debugging |
| **Total** | **53** | |

The category numbers keep folder browsing deterministic. They are not part of
skill invocation names.

## Default refinement workflow

```text
repository-onboarding
        |
        v
acceptance-criteria-design
        |
        v
architecture + API + data + conditional refinement
        |
        v
testing-strategy + technical-documentation
        |
        v
decision-record-management / architecture-decision-records
        |
        v
change-planning creates specs/<feature>/spec.md
        |
        v
specification approval
        |
        v
.NET and/or React implementation
        |
        v
code-review + CI quality gates
        |
        v
production-readiness
        |
        v
specification-lifecycle marks the work Implemented
```

[`refinement-workflow`](skills/01-workflow-governance/refinement-workflow/SKILL.md)
coordinates this sequence. It loads only the domain and conditional skills
whose triggers apply; it does not load the entire remaining catalog for every
task.

## Universal activation

`token-optimizer` applies a lightweight efficiency pass to every request. Its
common path protects correctness and user intent while reducing avoidable
context, tool, retry, and response cost. Detailed audit, instruction-design,
session, and runtime guidance remains behind conditional references so the
optimizer does not become a large recurring context burden itself.

Use the [Token Optimizer A/B benchmark controller](Automations/token-optimizer-ab-benchmark-prompt.md)
to compare isolated baseline and optimized agent sessions with deterministic
quality gates, native usage telemetry, and a mandatory greenfield project task
that starts in an empty folder.

## Conditional activation

Conditional skills are available from the beginning but remain dormant unless
the work requires them:

- `secure-code-review`: exposed APIs, access control, untrusted input,
  sensitive data, administrative operations, or multi-tenancy.
- `observability-engineering`: production services, background jobs, external
  integrations, or critical journeys.
- `secrets-and-configuration`: settings, tokens, connection strings, signing
  material, or environment-specific behavior.
- `application-threat-modeling`: new trust boundaries or meaningful security
  exposure.
- `backup-and-recovery-design`: durable or business-critical state.
- `performance-engineering`: explicit budgets or evidence of a performance
  problem.
- `dependency-upgrades`: changes to runtimes, frameworks, packages, analyzers,
  or build tools.
- `debugging-workflow`: bugs, regressions, intermittent failures, or unexplained
  behavior.

## Repository structure

```text
skills/
|-- CATALOG.md
|-- 01-workflow-governance/
|   |-- development-standards/
|   |   |-- SKILL.md
|   |   `-- references/
|   `-- <other-workflow-skills>/
|-- 02-dotnet-react/
|-- 03-backend-api/
|-- 04-database/
|-- 05-developer-experience/
|-- 06-architecture-strategy/
`-- 07-conditional-quality-operations/
```

Every skill folder contains a required `SKILL.md`. Supporting references exist
only when they improve progressive disclosure, such as shared development
standards and specification or decision templates.

## Finding a skill

Browse [skills/CATALOG.md](skills/CATALOG.md) for exact names, paths, and
activation triggers. Search names, descriptions, golden rules, or guardrails
with ripgrep:

```powershell
rg -n "authentication|migration|coverage|guardrails" skills
```

List all exact skill names:

```powershell
rg -n "^name:" skills -g SKILL.md
```

## Using the skills

Invoke a skill explicitly by its frontmatter name when you want to guarantee
its use, for example:

```text
$refinement-workflow refine this feature and create its specification
$database-schema-migrations review this code-first migration plan
$react-application-engineering implement the approved UI specification
```

Automatic discovery remains enabled by default. A skill being active never
grants permission to deploy, publish, migrate production data, rotate secrets,
or mutate external systems.

## Installing an individual skill

This repository uses category folders for source organization. Install an
individual skill by copying its complete folder—including `references`,
`scripts`, or `assets` when present—into your Codex skills directory under the
same skill name:

```text
<Codex skills directory>/development-standards/SKILL.md
<Codex skills directory>/development-standards/references/...
```

Use `$CODEX_HOME/skills` when `CODEX_HOME` is configured; otherwise Codex uses
the `.codex/skills` directory under the user profile. Do not copy only
`SKILL.md` when the skill links supporting resources.

## Generated refinement artifacts

Unless a repository already defines another convention, refinement produces:

```text
specs/<feature-name>/
|-- spec.md
`-- decisions/
    |-- DR-001-<decision>.md
    `-- ADR-001-<architecture-decision>.md
```

Specifications progress through `Draft`, `Approved`, `Implemented`,
`Superseded`, or `Rejected`. Material changes reopen the specification and
create or supersede the relevant decision records.

## Maintaining the catalog

When adding or changing a skill:

1. Keep the folder name identical to the frontmatter `name`.
2. Use lowercase hyphen-case and a discriminating `description`.
3. State what the skill changes, its golden rules, and its real guardrails.
4. Keep conditional detail in linked references rather than bloating the entry
   point.
5. Add the skill to [skills/CATALOG.md](skills/CATALOG.md) and update category
   counts here.
6. Validate names, metadata, relative links, unfinished placeholders, and
   repository whitespace before completion.

Do not add generic tutorials, repeated platform documentation, placeholder
folders, or rules created from a single isolated failure. Prefer narrow,
evidence-backed improvements from real usage.
