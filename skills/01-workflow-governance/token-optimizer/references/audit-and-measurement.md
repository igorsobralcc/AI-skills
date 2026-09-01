# Audit and Measurement

Use this workflow only when the user asks to audit or change token usage, cost, context capacity, prompts, agent instructions, skills, tools, or model routing. The every-request fast path does not require an audit.

## Define the objective

Agree on the outcome being optimized: more usable context, lower API cost, lower latency, fewer limits, better cache reuse, shorter outputs, or less repeated work. Record the quality floor and representative task set. Optimizing raw token count without a quality constraint invites false savings.

Define the scope and authority: current conversation, one repository, user-level setup, a fleet, an API application, or a particular workflow. Start read-only. Do not inspect unrelated accounts or private configuration, and do not mutate anything merely because the audit found waste.

## Establish a baseline

Prefer runtime-native usage data or the provider's supported tokenizer. Capture, when available:

- tokens loaded before the user request;
- uncached and cached input tokens;
- output and reasoning tokens;
- tool definitions and tool-result payloads;
- request, turn, tool-call, retry, and compaction counts;
- time to first token and end-to-end latency;
- model and reasoning configuration;
- task success, validation result, or user correction rate.

When exact counts are unavailable, use a consistent proxy such as UTF-8 bytes, characters, lines, serialized schema size, or command-output size. Label it as a proxy. Do not convert proxies to exact token or dollar claims without a tokenizer and current pricing source.

Run several representative tasks when variance is meaningful. Keep the workload, model, permissions, repository state, and cache condition comparable. Separate warm-cache and cold-cache measurements.

## Inventory the context path

Inspect only sources in scope and classify them:

| Source | Load behavior | Questions |
| --- | --- | --- |
| System and persistent instructions | fixed or hierarchical | Is it necessary, duplicated, stale, or misplaced? |
| Skill and agent descriptions | discovery-time | Does it route accurately with minimal metadata? |
| Skill bodies and references | selected or on demand | Is conditional detail deferred and discoverable? |
| Tool and MCP schemas | fixed, selected, or deferred | Are unused schemas loaded? Are descriptions actionable? |
| Repository context | retrieved | Are searches and reads targeted? Is content repeatedly reopened? |
| Conversation and memory | cumulative or compacted | Which state remains useful? What is stale narrative? |
| Tool output | episodic | Could filtering, parsing, or artifacts reduce replay? |
| Model output and reasoning | generated | Is verbosity or effort higher than the task requires? |

For each source, distinguish unavoidable contract cost, useful recurring context, useful conditional context, and avoidable waste.

## Rank changes

Estimate recurring burden before one-time burden:

```text
recurring input burden = loaded units per request * affected requests
tool-result burden      = returned units per call * calls
expected total cost     = input + output + reasoning + tool fees + retry cost
net benefit             = avoided recurring cost - added discovery and coordination cost
```

These are planning formulas, not claims of provider billing equivalence. Weight findings by frequency, magnitude, confidence, implementation risk, and quality impact.

Prioritize wrong-path prevention, duplicated always-loaded content, oversized tool schemas, repeated large outputs, stale conversation state, and needless retries. Treat file size, skill count, or MCP count as signals to investigate, not violations by themselves.

## Propose before changing

Present a compact plan containing:

| Finding | Evidence | Proposed change | Expected effect | Risk | Verification |
| --- | --- | --- | --- | --- | --- |

Separate measured facts from estimates. Name dependencies and behavior that could break. For configuration or persistent-instruction changes, preserve a recoverable copy or version-control diff, request approval when needed, and make the smallest coherent change.

Never archive, disable, or consolidate a skill or tool solely because invocation history is absent; telemetry may be incomplete and rare capabilities may be critical. Check references, dependencies, ownership, and fallback behavior.

## Verify

Repeat the baseline under comparable conditions. Report absolute values, relative change, measurement method, workload, cache state, and quality result. A useful comparison includes both savings and regressions.

Reject or revise a change when it saves tokens but reduces task success, violates a requirement, increases retries, hides evidence, or raises human effort beyond the benefit. Do not stack several changes before measuring when individual attribution matters.

Stop when the agreed target is met, remaining findings are below the measurement noise or expected implementation cost, or further work requires a user decision. Leave the user with the final configuration state, measured result, residual risks, and recovery path.

## Evidence discipline

Treat marketplace claims and single-project experiments as hypotheses, not universal guarantees. The reference implementations that informed this skill emphasize measurement, progressive disclosure, configuration audits, context management, and model routing; some also publish fixed thresholds and large percentage claims. Retain the mechanisms, but validate thresholds and savings in the user's own runtime and workload.

Maintainer baselines, not runtime dependencies:

- [alexgreensh/token-optimizer](https://github.com/alexgreensh/token-optimizer/blob/main/skills/token-optimizer/SKILL.md): measured configuration auditing, before/after verification, progressive disclosure, and runtime-specific workflows.
- [Stop Paying to Re-Derive: Token Optimization with Skills](https://www.youtube.com/watch?v=UuCIXio6vn4): the principle that reusable skills should prevent repeated derivation.
- [alexismunoz1/token-optimizer](https://lobehub.com/skills/alexismunoz1-token-optimizer): file organization, context management, model routing, and tool-surface reduction, treated as workload-dependent hypotheses rather than universal thresholds.
- [OpenAI model guidance](https://developers.openai.com/api/docs/guides/latest-model) and [Anthropic prompting guidance](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-templates-and-variables): current provider guidance for outcome-first prompts, caching, compaction, tool discovery, long context, and state continuity. Recheck these sources before changing platform-specific recommendations.
