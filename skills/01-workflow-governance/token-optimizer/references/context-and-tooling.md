# Context and Tooling Efficiency

Use this reference for long tasks, large repositories, verbose commands, repeated context loss, multi-agent work, or large tool catalogs.

## Retrieve in layers

Move from cheap structure to expensive content:

1. discover applicable instructions and repository boundaries;
2. list or search names and symbols;
3. inspect manifests, entry points, and the smallest representative files;
4. read exact regions around relevant matches;
5. widen only when evidence shows a cross-cutting dependency.

Prefer tools that filter before returning results. Search with precise patterns and path filters. Request only relevant log levels, test targets, columns, date ranges, result counts, or line ranges. When a tool cannot limit output, store the full result outside the conversation when allowed and return a concise summary plus the artifact location.

Do not repeatedly read unchanged content. Track evidence by stable file path, symbol, record ID, URL, or artifact rather than copying its full text into every turn.

## Control tool loops

Before each call, identify the decision it will enable. Batch independent, bounded reads when parallel execution is available. Keep dependent calls sequential. After each result, ask whether the core request can now be completed with adequate evidence.

Avoid:

- broad recursive listings after the relevant boundary is known;
- full build or test output when a failing target and tail are sufficient;
- repeated polling with no state change;
- opening every search result before ranking relevance;
- returning raw machine output when a parsed answer will do;
- tool calls whose result cannot change the next action.

Retain raw output when it is required for auditability, reproduction, or a deliverable. Token efficiency does not justify hiding evidence.

## Manage working state

For a long task, keep a compact checkpoint in the runtime's supported state mechanism or a user-approved workspace artifact:

```text
Goal:
Constraints and authorization:
Adopted decisions:
Completed actions and evidence:
Changed artifacts:
Verification status:
Open blockers or uncertainties:
Next concrete action:
```

Update the checkpoint at meaningful boundaries, before compaction when detectable, and before handing work to another context. Do not log conversational filler, abandoned hypotheses without future value, or raw outputs already stored elsewhere.

At a genuine task boundary, prefer a fresh context when the next task does not need the prior transcript. When continuity matters, resume from the compact checkpoint and authoritative artifacts rather than replaying the full conversation. Never clear or replace the user's session state without their request.

## Use agents economically

Delegation is useful when subtasks are independent, bounded, and can run concurrently or isolate unusually verbose evidence. It is wasteful when every agent must ingest the same large context, tasks are tightly dependent, or coordination exceeds the expected savings.

When delegation is permitted:

- give each agent the smallest sufficient brief and exact deliverable;
- share stable artifact locations instead of duplicating large content;
- avoid overlapping investigations;
- require concise findings with evidence pointers;
- stop or redirect work that has become redundant;
- integrate results once rather than restating every agent transcript.

Do not select a weaker model merely because a subtask sounds short. Match capability to ambiguity, risk, tool use, and verification needs.

## Design large tool surfaces

If the runtime supports deferred tool discovery or tool search, expose a small routing surface and load detailed schemas only when selected. Otherwise group tools by task and disable unused integrations only with user authorization and dependency checks.

Tool descriptions should state what the tool does, when to use it, required inputs, side effects, retry or idempotency behavior, and important errors. Remove examples or prose that do not improve correct selection or argument construction.
