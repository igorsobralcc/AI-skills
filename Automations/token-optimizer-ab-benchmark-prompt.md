# Token Optimizer A/B Benchmark Controller

Run a controlled, reproducible A/B benchmark that measures the end-to-end effect of the `token-optimizer` skill without sacrificing correctness or hiding its own recurring context cost.

Complete the benchmark automatically when the environment provides the required isolation, agent CLI, and telemetry. Do not ask routine questions. Stop and report a precise blocker rather than fabricating measurements, weakening isolation, changing global configuration, or claiming that a proxy is an exact token count.

## Objective

Compare two otherwise identical variants across representative coding-agent tasks:

- `baseline`: `token-optimizer` is neither installed, discoverable, injected, nor required in the measured subject session.
- `optimized`: the exact skill under test is installed and its every-request fast path is active in the measured subject session.

Measure the complete task, including persistent context, skill discovery, reasoning, tool schemas and results, retries, compaction, and final output. Determine whether the optimized variant reduces token or monetary expenditure while preserving task quality.

The controller running this prompt is not a measured subject. Launch every measured run as a fresh isolated child process or fresh runtime session. Never compare two turns inside this controller conversation.

## Inputs and defaults

Resolve these values before changing anything:

```text
RUNTIME: auto                         # auto | codex | claude-code | other
TOKEN_OPTIMIZER_SKILL_PATH: auto      # directory containing the skill's SKILL.md
SUBJECT_REPOSITORY: current directory # used only by the repository-comprehension task
REPETITIONS: 3
RANDOM_SEED: 20260901
CACHE_MODES: cold,warm
KEEP_RUN_WORKSPACES: true
MAX_PARALLEL_SUBJECTS: 1
```

Use a unique run ID. Create all benchmark state beneath a new dedicated root in the operating system's temporary directory, named `token-optimizer-benchmark-<run-id>`. Resolve and record its absolute path before writing. Never reuse, empty, recursively move, or recursively delete an existing directory.

Create a `results` directory under that root. Preserve the final report, manifests, raw telemetry, prompts, verifier output, and subject workspaces unless the user explicitly requests cleanup later.

If `TOKEN_OPTIMIZER_SKILL_PATH` is `auto`, discover candidates by exact folder name and a `SKILL.md` whose frontmatter name is `token-optimizer`. Prefer the repository-local skill over installed copies. If candidates differ, stop and report their paths and hashes rather than choosing silently.

## Non-negotiable validity rules

1. Keep the model, reasoning or effort setting, runtime version, permissions, tool and MCP availability, subject prompt, starting files, environment variables relevant to behavior, and verifier identical between paired variants.
2. The only intended independent variable is whether `token-optimizer` is available and active.
3. Use separate fresh sessions and separate workspace copies for every `(task, variant, repetition, cache mode)` run.
4. Do not use resume, fork, conversation replay, or a prior subject transcript for cold-cache runs.
5. Do not let output from one subject run enter another subject's prompt or workspace.
6. Do not run baseline and optimized subjects concurrently. Concurrency changes machine load, cache behavior, and rate-limit conditions.
7. Alternate or seeded-randomize variant order within each task and repetition. Record the actual order.
8. Never disable safety, approvals, or sandboxing to make automation easier. Give subjects only the permissions required inside their dedicated workspace.
9. Never modify the user's global Codex, Claude Code, shell, Git, MCP, or skill configuration. Construct isolated per-run configuration roots or use documented per-process configuration mechanisms.
10. Never use the user's API credentials in generated reports, command output, fixtures, or prompts. Redact secret-bearing environment values.
11. Do not interpret subscription rate-limit percentage as token count or dollar cost.
12. Treat marketplace savings claims as hypotheses. Publish only results measured in this benchmark.

If the runtime cannot prove variant isolation, mark the benchmark `INVALID_ISOLATION` and stop before paid subject runs.

## Phase 1: Detect capabilities

Detect the runtime using local executable help and visible environment signals. Record:

- runtime name and version;
- executable path;
- model and reasoning or effort setting;
- supported non-interactive invocation;
- supported structured or event-stream output;
- native usage, cache, cost, duration, turn, and session identifiers;
- skill installation and invocation mechanism;
- isolated configuration mechanism;
- context reset or fresh-session mechanism;
- tokenizer or input-token-counting mechanism, if available.

Do not assume that an API capability exists in the desktop or CLI product.

### Codex adapter

Prefer `codex exec --json` for measured non-interactive runs when supported. Use an explicit working directory and workspace-write sandbox. Use the installed version's documented profile or isolated configuration behavior to create both variants.

Collect native JSONL events. When the installed Codex version persists an exact session rollout with `event_msg.payload.type == "token_count"`, associate it with the subject session ID and capture the final cumulative `total_token_usage`, including:

```text
input_tokens
cached_input_tokens
cache_write_input_tokens
output_tokens
reasoning_output_tokens
total_tokens
model_context_window
```

Treat the rollout schema as version-dependent. Validate every field before using it. Never select a session merely because it is the newest when another Codex run may be active. If native CLI events provide authoritative usage directly, prefer them over private session storage.

### Claude Code adapter

Prefer non-interactive execution with structured output, for example `claude -p ... --output-format json`, after confirming the installed version's help. Capture native fields such as total cost, duration, API duration, turn count, result status, and session ID. Use `stream-json` with verbose output only when needed for granular token and cache usage.

If exact token fields are unavailable, use the runtime's reported total cost as the primary financial measure and record byte counts, turns, tool calls, and duration as proxies. Do not reverse-engineer exact tokens from dollar cost when caching, tools, or changing prices make the conversion ambiguous.

### Other runtimes

Use the runtime's supported fresh-session, isolated-config, structured-output, and usage facilities. If exact token or cost telemetry is absent, continue only if a consistent disclosed proxy can answer a narrower question. Mark the result `PROXY_ONLY` and do not claim exact token savings.

## Phase 2: Build isolated variants

Create two minimal configuration roots from the same manifest.

For `baseline`:

- exclude the `token-optimizer` directory and its discovery metadata completely;
- exclude any global instruction that requires or paraphrases the optimizer;
- keep every unrelated skill, instruction, tool, permission, and setting identical to `optimized`;
- do not replace the optimizer with a baseline-specific instruction.

For `optimized`:

- install an exact copy or isolated link to `TOKEN_OPTIMIZER_SKILL_PATH` using the runtime's supported skill location;
- preserve the skill's files and relative paths;
- enable normal implicit discovery when supported;
- add the smallest runtime-supported requirement needed to guarantee the skill's every-request fast path, only inside the isolated configuration;
- do not add extra optimization instructions outside the skill.

Generate a canonical manifest for each variant. Normalize expected path differences, then compare the manifests. Fail if they differ outside the allowed optimizer entries.

Record SHA-256 hashes for the tested `SKILL.md`, references, runtime configuration, task prompts, fixture manifests, and verifier definitions.

## Phase 3: Prove isolation before benchmarking

Run one zero-side-effect preflight subject for each variant using the same prompt:

```text
Report only the names and absolute source paths of skills and persistent instruction files that the runtime made available for this request. Do not inspect unrelated home-directory content and do not perform the benchmark tasks.
```

Combine the subject response with controller-observable runtime evidence. The baseline must contain no optimizer name, description, body, reference, symlink, or enforcement instruction. The optimized variant must contain the expected skill hash and activation instruction.

Self-report alone is not sufficient proof. If the runtime cannot expose observable configuration or injection evidence, state the limitation and require a supported isolation method before continuing.

## Phase 4: Prepare deterministic fixtures

Prepare fixtures once outside all measured sessions. Fixture creation is controller setup and must not be charged to either variant. Record a manifest of every file and its SHA-256 hash. Copy the pristine fixture into a new run workspace before each subject invocation.

Choose one installed application stack before creating fixtures and keep it fixed across variants. Prefer, in order:

1. the stack explicitly configured by the user;
2. a stack already used by `SUBJECT_REPOSITORY`;
3. a locally installed stable .NET, Node.js/TypeScript, or Python toolchain with offline-capable project initialization and testing.

Do not download packages merely to create the benchmark. If no suitable offline-capable toolchain exists, stop with `BLOCKED_TOOLCHAIN`.

Create verifiers that run without an AI model. Each verifier must produce structured JSON containing pass/fail, checks executed, failures, and duration.

## Phase 5: Benchmark tasks

Use the exact task text for both variants. Substitute only the normalized workspace placeholder. Do not reveal expected defects, verifier internals, scoring keys, or the other variant's result to the subject.

### T01 — Greenfield project in an empty folder

Before each run, create a new directory named `workspace` and verify it contains zero entries. If it is not empty, fail the run; do not clean or reuse it.

Subject prompt:

```text
Create a new project from scratch in the provided empty workspace.

Build a command-line task tracker named TaskLedger using the selected local stack. It must support:

- `add <description>`: create a task with a generated stable ID and UTC creation timestamp;
- `list`: show all tasks in a deterministic order and clearly distinguish pending and completed tasks;
- `complete <id>`: mark an existing task complete and return a non-zero exit code for an unknown ID;
- durable local JSON persistence using an application-owned data file;
- rejection of blank descriptions without corrupting existing data;
- deterministic automated tests for the core behavior and failure cases;
- a concise README containing prerequisites, build, test, and usage commands.

Keep dependencies minimal and use only resources already available locally. Do not access external services. Follow the selected stack's normal project conventions. Complete the implementation, run the relevant build and tests, and report the files created, verification commands, and any remaining limitations.
```

Verifier requirements:

- workspace was empty before subject execution;
- project manifest and source files exist;
- documented build and test commands execute successfully;
- automated tests pass;
- add, list, persistence, completion, unknown-ID, and blank-description behavior pass independent black-box checks;
- README commands match implemented behavior;
- no files were written outside the subject workspace.

### T02 — Focused defect correction

Create a small project in the selected stack containing an invoice calculator with independent tests. Seed exactly these behavioral defects without documenting them in the subject prompt:

- tax is applied before discount instead of after discount;
- binary floating-point arithmetic creates incorrect currency rounding;
- a negative quantity is accepted;
- an unknown discount code silently behaves like no discount.

Include unrelated files and passing tests so targeted discovery matters. Preserve a hidden verifier separate from the visible tests.

Subject prompt:

```text
Diagnose and fix the failing invoice-calculation behavior in this repository. Preserve the public interface and do not weaken, delete, skip, or rewrite tests merely to obtain a passing result. Use currency-safe arithmetic, validate invalid inputs, run the most relevant verification, and summarize the root causes and changed files.
```

Score visible and hidden tests, public-interface compatibility, unrelated-file changes, and accuracy of the root-cause summary.

### T03 — Repository comprehension

Use a read-only copy of `SUBJECT_REPOSITORY` or, when it is unsuitable, a deterministic multi-module fixture containing at least three modules, tests, CI configuration, and hierarchical instruction files.

Subject prompt:

```text
Produce a concise repository map for a new contributor. Identify the technologies, module boundaries, authoritative instructions, build and test commands, CI entry points, generated-code boundaries, and the smallest set of files that should be read before changing behavior. Support each material claim with a file or symbol path. Do not modify the repository.
```

Score factual accuracy against the fixture manifest, evidence-path validity, completeness of required categories, unsupported claims, and output length.

### T04 — Large-output incident diagnosis

Generate a deterministic synthetic log large enough to punish unbounded reading. Include routine noise, repeated downstream failures, and one earlier causal chain that identifies a resource-exhaustion trigger, the originating component, and the first actionable error. Store the expected causal chain in the hidden verifier.

Subject prompt:

```text
Diagnose the incident represented by the supplied logs. Identify the originating failure rather than the repeated downstream symptoms, cite the smallest useful evidence locations, explain the causal chain, and recommend one immediate mitigation plus one durable corrective action. Do not modify the fixture.
```

Score root-cause accuracy, causal ordering, evidence precision, false claims, bytes returned by tools, tool-call count, and final-answer length.

### T05 — Instruction compression with behavioral preservation

Create a verbose instruction fixture containing exact duplication, obsolete advice explicitly marked as superseded, conditional procedures, examples, safety and authorization invariants, and project-specific commands. Maintain a hidden checklist of every rule that must survive.

Subject prompt:

```text
Optimize the supplied persistent AI instruction file for recurring context efficiency. Preserve all active safety, authorization, behavioral, project, and verification requirements. Remove duplication and superseded guidance, convert repeated cases into decision rules, and move substantial conditional detail into discoverable references when useful. Validate relative links and provide before/after size measurements plus a concise account of preserved invariants and trade-offs.
```

Score retained active requirements, removal of obsolete material, link validity, routing clarity, before/after measured size, and unsupported savings claims.

## Phase 6: Execute the matrix

Construct the run matrix for every task, variant, repetition, and cache mode.

For each run:

1. Create a new uniquely named run directory.
2. Copy the pristine fixture or create the verified empty T01 workspace.
3. Record the starting manifest and machine timestamp.
4. Launch one fresh subject session with the exact prompt and isolated variant configuration.
5. Capture stdout, stderr, structured events, exit status, session ID, duration, and native usage.
6. Run the deterministic verifier after the subject exits.
7. Record the ending manifest and all files written outside the expected output boundary, if any.
8. Normalize paths only in the analysis copy; preserve raw evidence unchanged.
9. Mark invalid, timed-out, rate-limited, approval-blocked, or telemetry-incomplete runs explicitly. Do not silently retry.

For warm-cache measurement, warm only the stable, identical portions allowed by the runtime, then execute a fresh subject session. Do not use a completed A run to warm B or vice versa. Record the actual cache-write and cache-read evidence.

Use one retry only for a documented transient infrastructure failure. The retry is a replacement run, not part of task performance, and must retain both attempts in the report.

## Phase 7: Normalize metrics

Create one record per run with at least:

```text
run_id
runtime
runtime_version
model
reasoning_or_effort
task_id
variant
repetition
cache_mode
execution_order
status
quality_pass
quality_score
input_tokens
cached_input_tokens
cache_write_input_tokens
uncached_input_tokens
output_tokens
reasoning_tokens
total_tokens
reported_cost
cost_currency
tool_calls
tool_result_bytes
turns
retries
compactions
duration_ms
subject_output_bytes
session_id
telemetry_source
telemetry_is_exact
workspace_manifest_hash
prompt_hash
config_hash
```

When the provider defines cached tokens as a subset of input tokens, calculate:

```text
uncached_input_tokens = input_tokens - cached_input_tokens
```

Do not add reasoning tokens to output tokens when reasoning is already an output-token subset. Prefer the provider's `total_tokens` field. Keep unavailable fields null rather than zero.

Compute paired deltas only between valid runs with matching task, repetition, cache mode, model, prompt hash, starting workspace hash, and non-optimizer configuration hash:

```text
token_delta = optimized_total_tokens - baseline_total_tokens
token_savings_percent =
  (baseline_total_tokens - optimized_total_tokens)
  / baseline_total_tokens * 100

cost_delta = optimized_reported_cost - baseline_reported_cost
cost_savings_percent =
  (baseline_reported_cost - optimized_reported_cost)
  / baseline_reported_cost * 100
```

Calculate medians and ranges by task category, cache mode, and overall. Do not average percentages directly; calculate aggregate savings from aggregate paired totals. With only three repetitions, present observations rather than claims of statistical significance.

## Phase 8: Quality gate

Token reduction is accepted only when quality is non-inferior.

- Automated verifier pass/fail outranks subjective brevity.
- A run that fails required behavior cannot contribute positive savings.
- A run that modifies forbidden files, weakens tests, invents evidence, or violates authorization is a quality failure.
- Report quality-score differences beside token and cost differences.
- Separate `gross token change` from `quality-qualified savings`.
- If optimized quality is lower, report the token reduction as invalidated and identify the regression.
- If the skill increases cost on simple tasks but reduces it on longer tasks, report the crossover honestly rather than hiding either result.

Do not establish a universal success threshold after seeing the data. If no threshold was supplied, use this decision:

```text
PASS:
  all mandatory task verifiers pass in both variants,
  optimized aggregate quality is not lower,
  and optimized aggregate exact cost or total tokens is lower.

INCONCLUSIVE:
  isolation or exact telemetry is incomplete,
  results are within observed run-to-run variation,
  or baseline quality failures prevent a fair comparison.

FAIL:
  optimized aggregate quality is lower,
  or optimized aggregate expenditure is not lower despite comparable quality.
```

## Phase 9: Deliverables

Write these artifacts beneath `results`:

```text
benchmark-manifest.json
capabilities.json
variant-isolation.json
tasks.json
fixture-manifest.json
run-order.json
runs.jsonl
paired-results.csv
summary.json
report.md
```

`report.md` must include:

1. outcome first: `PASS`, `FAIL`, `INCONCLUSIVE`, or `INVALID_ISOLATION`;
2. tested skill path and SHA-256 hash;
3. runtime, version, model, effort, permissions, and tool surface;
4. isolation evidence and known limitations;
5. task-by-task baseline versus optimized quality, tokens, cost, calls, and duration;
6. cold-cache and warm-cache results separately;
7. aggregate paired medians, ranges, absolute deltas, and percentages;
8. optimizer overhead on T01 and other short or setup-heavy work;
9. quality regressions, invalid runs, retries, and missing telemetry;
10. evidence paths for raw events and verifier results;
11. a conclusion limited to the tested runtime, model, workload, and skill hash;
12. recommended next experiment, if any.

Never include secrets, hidden reasoning, full private prompts supplied by the runtime, unrelated session content, or raw home-directory configuration in the report.

## Completion response

When finished, respond concisely with:

- benchmark outcome;
- valid paired-run count;
- aggregate quality-qualified token and cost change;
- whether T01 successfully created and verified a project in an empty folder;
- largest improvement and largest regression;
- exact path to `report.md`;
- blockers or telemetry limitations.

Do not claim success merely because the optimized responses were shorter.
