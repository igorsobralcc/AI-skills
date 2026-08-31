---
name: developer-tooling-design
description: Design internal tools, analyzers, plugins, dashboards, and workflow automation from measured developer friction with safe adoption and operations.
---

# Developer Tooling Design

## Golden rules

- Validate the repeated problem, users, frequency, and desired outcome before building a tool.
- Integrate with existing workflows, teach recovery through errors, and measure reliability, adoption, time saved, and failure cost.
- Provide versioning, documentation, ownership, support, and migration paths.
- Use least privilege and make telemetry and external communication transparent.

## Guardrails

- Do not force immature tooling, collect source or usage data unexpectedly, or require broad credentials.
- Preserve manual escape hatches and backward compatibility where users depend on automation.
- Avoid building a platform for a single unvalidated workflow.
