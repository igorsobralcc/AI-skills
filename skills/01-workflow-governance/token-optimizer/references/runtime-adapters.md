# Runtime Adapters

Use visible runtime information first. Do not probe private home-directory configuration on every ordinary request. If the runtime is unknown, apply the generic adapter and avoid invented commands, paths, model names, or pricing.

Product behavior changes. Verify current official documentation or local help before making a consequential runtime-specific recommendation.

## Generic agent runtime

- Follow the runtime's actual instruction precedence and authorization model.
- Keep universal instructions short; load task and domain guidance on demand.
- Prefer native search, structured output, state, caching, compaction, and deferred-tool features when available.
- Use capability tiers rather than hardcoded model names: lightweight retrieval or transformation, balanced tool work, and high-reasoning complex or high-risk work.
- Change the model, reasoning level, verbosity, tool set, or session state only when the interface permits it and the user has authorized material configuration changes.
- If token counters are unavailable, measure characters, bytes, lines, tool payload sizes, turn count, wall time, and retries as disclosed proxies.

## Claude Code

Keep `CLAUDE.md` focused on stable project guidance that materially changes work: important architecture, verified commands, repository conventions, and non-obvious constraints. Put personal cross-project preferences in the supported user-level location. Prefer nested project instructions for subtree-specific rules so unrelated work does not load them.

Use imports and linked files deliberately. An import that loads unconditionally is not progressive disclosure merely because it lives in another file. Inspect the runtime's memory view or equivalent to confirm what is actually loaded.

For skills:

- make the description an accurate router;
- keep the common workflow in `SKILL.md`;
- link conditional references where they become necessary;
- avoid copying full platform manuals or large examples into the skill;
- test both triggering and non-triggering requests.

For long sessions, use the installed version's context inspection, compaction, clearing, memory, or checkpoint facilities when available. Preserve the goal, decisions, completed work, evidence, changed files, verification state, blockers, and next action before a context transition. A fresh session can be cheaper and cleaner when authoritative state already exists in files and the previous dialogue is no longer useful.

Use subagents for truly independent work or to isolate large evidence only when the runtime and governing instructions permit them. Account for the duplicated prompt and repository context each agent receives.

Do not prescribe `haiku`, `sonnet`, or `opus` as permanent defaults without checking the current models, billing mode, task risk, and measured quality. Route by capability and validate on representative work.

## OpenAI Codex

Keep `AGENTS.md` and equivalent project instructions scoped by repository hierarchy. Place stable cross-repository behavior at the appropriate user layer, repository rules at the repository root, and narrower rules close to the files they govern. Avoid duplicating the same rule at several levels.

Codex skills should use concise discovery metadata and progressive disclosure. In `agents/openai.yaml`, leave implicit invocation enabled for ordinary discoverable skills; make a skill explicit-only only when the user requests that behavior. A skill intended for every request still needs a small common path so its own recurring context cost remains low.

Prefer targeted repository discovery, bounded command output, and direct artifact links. Keep user-visible tool preambles brief and useful for multi-step work; do not repeat the same status in the final answer.

Use compaction and task checkpoints for long-running work. Preserve concrete state rather than narrative history. Use parallel agents only when governing instructions permit delegation and the subtasks are independently valuable.

When building with the OpenAI API rather than operating inside Codex:

- keep stable prompt prefixes consistent and dynamic content later to improve eligible prompt-cache reuse;
- use structured outputs instead of explaining machine schemas in prose when appropriate;
- defer large tool catalogs with tool search when supported;
- preserve conversation state with the supported response-state mechanism;
- tune reasoning effort and output verbosity independently against representative evaluations;
- track cached input, uncached input, output, reasoning, tool calls, latency, retries, and task success.

Do not assume an API feature is exposed in every Codex surface.

## Other coding agents

Map the same principles to the runtime's native files and controls rather than creating Claude- or Codex-shaped configuration:

1. identify which instructions and tool schemas load on every request;
2. identify hierarchical or conditional instruction mechanisms;
3. identify context inspection, compaction, and reset behavior;
4. identify model, reasoning, verbosity, and tool-discovery controls;
5. verify permission and recovery behavior before configuration changes;
6. measure with the runtime's own usage data when available.

If a feature is absent, use a simple portable artifact such as a concise progress file instead of simulating a complex framework.
