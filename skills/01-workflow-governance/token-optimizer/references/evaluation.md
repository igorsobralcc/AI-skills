# Evaluation and accounting

This protocol is independent of other optimizer packages. No runtime helper, telemetry collector, proxy, or paid benchmark is included. Package bytes and local token estimates are not invocation cost measurements.

## Freeze and execute

1. Freeze original prompts/turns, authoritative facts, exact literals, required information, forbidden mutations, acceptance IDs, and rubric before generation. Keep development examples separate from held-out cases. Record hashes/revisions. Cases used to tune instructions become development cases and must be replaced in the held-out set.
2. Compare baseline without the skill to lite, full, ultra, and off with the skill available. Off checks disabling behavior and may still incur discovery cost. Use identical model/runtime versions, settings, tool permissions, task state, and declared cache conditions. Run at least three paired repetitions per scenario, alternating baseline/candidate order. Record actual order, not intended order.
3. Include multi-turn activation/restoration and complete tasks. Preserve raw prompts, outputs, errors, tool calls, clarification turns, and native usage. Failed runs and retries remain in the record. Do not add samples merely to obtain favorable results; name the remaining uncertainty first.
4. Review independently against facts, preferably blinded to condition. Evaluate task fulfillment, semantics, exact material, language/schema, then style. Review token counts separately. Critical/major defects block release; indeterminate is not a pass.
5. Report every scenario before aggregates: sample sizes, paired absolute counts, reductions, variation (range and standard deviation when available), defects, exclusions, missing evidence, and scope limits. A workload-weighted aggregate requires weights frozen before results; otherwise use an explicitly unweighted aggregate.

## Record contract

Use UTF-8 JSON Lines: one run object per line, unique `run_id`. Store referenced artifacts beside the manifest using relative paths. Preserve raw provider records without rewriting them. Logical fields below are required; unavailable values are JSON null, never invented zeros. Empty arrays mean observed absence, not unavailable data.

| Fields | Meaning |
| --- | --- |
| `case_id`, `pair_id`, `run_id`, `condition`, `repetition`, `execution_order` | Stable case and pair identities; condition baseline/lite/full/ultra/off; repetition starts at 1; actual ordered position |
| `model_version`, `runtime_version`, `instruction_revision`, `source_revision` | Exact versions or null with a missing-evidence reason |
| `tool_permissions`, `settings`, `cache_conditions` | Actual execution conditions, including cache uncertainty |
| `started_at`, `ended_at`, `completion_status`, `artifact_paths`, `errors` | ISO-8601 timestamps with offsets, actual completion, relative raw artifact paths, failures |
| `provider_usage`, `usage_semantics`, `parent_run_id`, `included_child_run_ids` | Native payload or reference, field meanings/overlap, aggregation ownership |
| `local_tokenizer`, `estimated_usage` | Tokenizer name and version plus estimates, kept separate from native measurements |
| `quality` | Verdict, defect categories, reviewer identity/type, supporting excerpts and rubric evidence |
| `missing_evidence` | Explicit reasons for every unavailable material measurement |

The manifest declares fixture revision, conditions, three or more repetitions, order schedule, workload weights or unweighted policy, counter semantics, claimed workflow boundary, and exclusions policy before generation. Reject duplicate run IDs, mismatched task state/settings, missing counterpart, incomplete output, or incompatible counts for the affected metric. An invalid native-total pair can still have a separately labeled valid output-estimate comparison; never silently generalize it.

## Calculate without overlap

Reduction is `(baseline - candidate) / baseline * 100` only with compatible counts and nonzero baseline. Report absolute counts alongside it. Zero baseline makes percentage undefined; negative reduction is a regression. Sum compatible absolute counts before computing a pooled reduction; do not silently average percentages. Keep per-case results visible.

Complete-task input includes actual skill discovery metadata, entrypoint and loaded references, repeated injections, history, tool results, and any additional turns. Include output, retries, and child-agent usage belonging to the claimed scope. A parent aggregate that already includes a child must not have that child added again. If reasoning is included in output, do not add reasoning again. Cache reads/writes are subcategories or separate categories according to documented provider semantics; never guess. Unknown semantics invalidate affected totals.

Report output-only reduction, complete-task usage, latency, tool calls, and monetary cost separately. A dated provider price schedule and its billing/cache semantics are necessary for monetary estimates; output reduction is not equal billing reduction. Local tokenizer estimates require name/version and source text; never label them native telemetry. Native counts unavailable for either condition mean native savings are unknown.

Examples using synthetic arithmetic only: baseline input 1000/output 200 and candidate input 1400/output 100 yield 50% output reduction but total usage grows from 1200 to 1500 (reduction -25%). Output 100 including reasoning 30 contributes 100, not 130. Parent total 800 including child total 200 contributes 800, not 1000. These are accounting fixtures, not product performance results.

## Release and limitations

All hard semantic, authorization, schema, and task-completion cases must pass; package metadata and links must validate. Retain quality failures even when excluding pairs from a numerical aggregate. Report offline evaluator overhead separately from production-task usage, and include evaluators if the claimed workflow actually requires them. No proven-savings claim without positive measured results and complete accounting for the stated workload. Without that evidence, describe this solely as a response-style capability. Do not mark the specification Implemented while required evidence remains missing.
