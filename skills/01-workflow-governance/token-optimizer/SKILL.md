---
name: token-optimizer
description: Apply a lightweight token- and context-efficiency pass to every AI-assisted request without reducing correctness, completeness, safety, or user intent; also audit prompts, instructions, skills, tools, and sessions when optimization is the task. Use for every request in any AI tool, with Claude Code and Codex-specific guidance when detected.
---

# Token Optimizer

Minimize the total resources required to complete the user's actual goal while preserving outcome quality. Count input, output, reasoning, tool payloads, repeated work, cache misses, retries, latency, and human follow-up as costs. A shorter response that causes confusion or another turn is not an optimization.

## Every-request fast path

Apply this silently unless the user asks about optimization or a trade-off changes the result.

1. Extract the required outcome, constraints, evidence, side-effect boundaries, and output shape. Do not optimize away an explicit requirement.
2. Reuse trustworthy context already present. Acquire only the smallest additional context that can resolve the next decision.
3. Prefer targeted search, narrow reads, batched independent lookups, and output limits at the source. Do not load whole trees, manuals, logs, or tool catalogs speculatively.
4. Stop investigating when the core request can be answered or completed with adequate evidence. Do not spend tokens proving facts that do not affect the outcome.
5. Lead with the result. Match the user's requested detail; omit restatement, process narration, duplicated evidence, and decorative structure that do not improve comprehension.
6. Before finishing, check that economy did not remove required validation, citations, caveats, safety controls, accessibility, or important failure behavior.

For multi-step work, maintain a compact working state containing only the goal, adopted decisions, material constraints, completed actions, evidence locations, unresolved blockers, and next action. Do not repeatedly recap it to the user.

## Optimization order

Prefer reductions in this order because upstream waste multiplies downstream cost:

1. Prevent wrong-path work, retries, and unnecessary tool or model calls.
2. Reduce always-loaded instructions, schemas, and duplicated context.
3. Retrieve less data and constrain verbose command or tool output.
4. Preserve useful state across long tasks and discard stale state at task boundaries.
5. Make the final answer no longer than the user and outcome require.
6. Route to a cheaper or faster model only when the environment permits it and representative evidence shows quality remains acceptable.

## Decision rules

- Correctness, user intent, safety, authorization, and required evidence outrank token savings.
- Use progressive disclosure: concise routing metadata, essential core instructions, and conditional references loaded only when needed.
- Do not impose universal file-length, tool-count, turn-count, or model-tier limits. Use measured burden, cohesion, retrieval patterns, and task risk.
- Do not split cohesive code merely to reduce file size; extra navigation can cost more on cross-cutting work.
- Use parallel agents only when supported, authorized, and the benefit of independent parallel work exceeds duplicated context and coordination cost.
- Never claim a percentage, dollar saving, or token count without a named measurement method and baseline. Label estimates and their assumptions.
- Do not mutate agent configuration, archive instructions, disable tools, change models, or clear session state unless the user requested that action. Inspect dependencies, preserve a recovery path, and show the proposed change first when practical.
- Do not expose hidden reasoning or private context. Report observable measurements and actionable findings.

## Conditional guidance

- For a prompt, system instruction, memory file, skill, or tool-description change, read [instruction-design.md](references/instruction-design.md).
- For long sessions, large repositories, verbose tools, or repeated context loss, read [context-and-tooling.md](references/context-and-tooling.md).
- For Claude Code, Codex, or another runtime-specific recommendation, read [runtime-adapters.md](references/runtime-adapters.md). Verify current product behavior before prescribing commands or model names.
- When the user asks to audit, measure, reduce cost, or optimize an AI setup, read [audit-and-measurement.md](references/audit-and-measurement.md) and use its measured workflow.

Ordinary requests should complete through the fast path without loading every reference.
