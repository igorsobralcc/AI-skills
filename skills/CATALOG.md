# Skill Catalog

Search all skill instructions with `rg -n "term" skills`. Skill folders are
grouped for browsing; frontmatter names are the exact invocation names.

## Workflow and governance

| Skill | Use when |
| --- | --- |
| [`refinement-workflow`](01-workflow-governance/refinement-workflow/SKILL.md) | Coordinating refinement through a final specification |
| [`development-standards`](01-workflow-governance/development-standards/SKILL.md) | Implementing, scaffolding, or reviewing code |
| [`repository-onboarding`](01-workflow-governance/repository-onboarding/SKILL.md) | Entering an unfamiliar repository |
| [`acceptance-criteria-design`](01-workflow-governance/acceptance-criteria-design/SKILL.md) | Defining observable outcomes and boundaries |
| [`change-planning`](01-workflow-governance/change-planning/SKILL.md) | Creating the final version-controlled spec |
| [`specification-lifecycle`](01-workflow-governance/specification-lifecycle/SKILL.md) | Approving, reconciling, completing, or superseding specs |
| [`decision-record-management`](01-workflow-governance/decision-record-management/SKILL.md) | Recording an adopted consequential decision |
| [`architecture-decision-records`](01-workflow-governance/architecture-decision-records/SKILL.md) | Recording a durable architecture decision |
| [`testing-strategy`](01-workflow-governance/testing-strategy/SKILL.md) | Mapping tests and feature-specific coverage |
| [`technical-documentation`](01-workflow-governance/technical-documentation/SKILL.md) | Planning or reconciling documentation for a change |
| [`code-review`](01-workflow-governance/code-review/SKILL.md) | Reviewing implementation conformance and risk |
| [`ci-cd-pipeline-engineering`](01-workflow-governance/ci-cd-pipeline-engineering/SKILL.md) | Automating quality and delivery gates |
| [`production-readiness`](01-workflow-governance/production-readiness/SKILL.md) | Assessing production evidence and residual risk |
| [`help`](01-workflow-governance/help/SKILL.md) | Finding an available skill or completing an underspecified request |

## .NET and React

| Skill | Use when |
| --- | --- |
| [`dotnet-application-engineering`](02-dotnet-react/dotnet-application-engineering/SKILL.md) | Implementing or reviewing .NET/C# code |
| [`aspnet-api-design`](02-dotnet-react/aspnet-api-design/SKILL.md) | Implementing or reviewing ASP.NET APIs |
| [`entity-framework-migrations`](02-dotnet-react/entity-framework-migrations/SKILL.md) | Mapping or migrating an EF Core database |
| [`react-application-engineering`](02-dotnet-react/react-application-engineering/SKILL.md) | Implementing or reviewing React/TypeScript code |

## Backend and API

| Skill | Use when |
| --- | --- |
| [`backend-application-design`](03-backend-api/backend-application-design/SKILL.md) | Selecting proportional backend architecture |
| [`api-contract-design`](03-backend-api/api-contract-design/SKILL.md) | Designing or evolving an external contract |
| [`event-driven-architecture`](03-backend-api/event-driven-architecture/SKILL.md) | Asynchronous decoupling or event history is justified |
| [`distributed-systems-reliability`](03-backend-api/distributed-systems-reliability/SKILL.md) | Remote dependencies require failure design |
| [`background-job-design`](03-backend-api/background-job-design/SKILL.md) | Queued or scheduled work is required |
| [`authentication-authorization-design`](03-backend-api/authentication-authorization-design/SKILL.md) | Identity or access control changes |
| [`multi-tenant-application-design`](03-backend-api/multi-tenant-application-design/SKILL.md) | Tenant isolation is a real requirement |
| [`caching-strategy`](03-backend-api/caching-strategy/SKILL.md) | Evidence justifies caching |
| [`integration-adapter-design`](03-backend-api/integration-adapter-design/SKILL.md) | Integrating an external provider or system |

## Database engineering

| Skill | Use when |
| --- | --- |
| [`relational-database-design`](04-database/relational-database-design/SKILL.md) | Designing relational data and invariants |
| [`database-schema-migrations`](04-database/database-schema-migrations/SKILL.md) | Planning or reviewing schema evolution |
| [`sql-query-review`](04-database/sql-query-review/SKILL.md) | Reviewing SQL or ORM-generated query behavior |

## Developer experience

| Skill | Use when |
| --- | --- |
| [`local-development-experience`](05-developer-experience/local-development-experience/SKILL.md) | Improving setup and feedback loops |
| [`repository-automation`](05-developer-experience/repository-automation/SKILL.md) | Automating repository workflows or policy |
| [`cli-design`](05-developer-experience/cli-design/SKILL.md) | Designing or changing a CLI |
| [`scaffolding-and-code-generation`](05-developer-experience/scaffolding-and-code-generation/SKILL.md) | Repeated structures justify generation |
| [`monorepo-engineering`](05-developer-experience/monorepo-engineering/SKILL.md) | A monorepo exists or is being evaluated |
| [`developer-tooling-design`](05-developer-experience/developer-tooling-design/SKILL.md) | Building internal engineering tools |

## Architecture and strategy

| Skill | Use when |
| --- | --- |
| [`service-boundary-analysis`](06-architecture-strategy/service-boundary-analysis/SKILL.md) | Evaluating service seams |
| [`modular-monolith-design`](06-architecture-strategy/modular-monolith-design/SKILL.md) | Designing enforceable modules in one deployable |
| [`architecture-diagrams`](06-architecture-strategy/architecture-diagrams/SKILL.md) | A visual architecture question needs answering |
| [`technical-debt-assessment`](06-architecture-strategy/technical-debt-assessment/SKILL.md) | Prioritizing evidenced technical debt |
| [`build-vs-buy-evaluation`](06-architecture-strategy/build-vs-buy-evaluation/SKILL.md) | Comparing internal development and adoption |
| [`platform-engineering`](06-architecture-strategy/platform-engineering/SKILL.md) | Designing internal self-service capabilities |
| [`sdk-and-client-library-design`](06-architecture-strategy/sdk-and-client-library-design/SKILL.md) | Designing a client library or SDK |

## Conditional quality and operations

| Skill | Trigger |
| --- | --- |
| [`secure-code-review`](07-conditional-quality-operations/secure-code-review/SKILL.md) | Exposed APIs, access control, untrusted input, sensitive data, admin, or tenancy |
| [`observability-engineering`](07-conditional-quality-operations/observability-engineering/SKILL.md) | Production services, jobs, integrations, or critical journeys |
| [`secrets-and-configuration`](07-conditional-quality-operations/secrets-and-configuration/SKILL.md) | Settings, credentials, tokens, keys, or environment behavior |
| [`application-threat-modeling`](07-conditional-quality-operations/application-threat-modeling/SKILL.md) | New trust boundaries or consequential security exposure |
| [`backup-and-recovery-design`](07-conditional-quality-operations/backup-and-recovery-design/SKILL.md) | Durable or business-critical state |
| [`performance-engineering`](07-conditional-quality-operations/performance-engineering/SKILL.md) | Explicit performance requirements or evidence of a problem |
| [`dependency-upgrades`](07-conditional-quality-operations/dependency-upgrades/SKILL.md) | Runtime, framework, package, analyzer, or tool versions change |
| [`debugging-workflow`](07-conditional-quality-operations/debugging-workflow/SKILL.md) | Bugs, regressions, intermittent failures, or unexplained behavior |

## Dependency flow

```text
repository-onboarding
        -> acceptance-criteria-design
        -> architecture/API/data/conditional refinement
        -> testing-strategy + technical-documentation
        -> decision-record-management / architecture-decision-records
        -> change-planning creates the specification
        -> .NET and/or React implementation
        -> code-review + CI gates
        -> production-readiness
        -> specification-lifecycle marks Implemented
```
