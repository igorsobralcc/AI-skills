# Instruction and Skill Design

Use this reference when changing prompts, persistent instructions, memory files, skills, agent definitions, or tool descriptions.

## Design for the instruction lifecycle

Classify each instruction before deciding where it belongs:

| Class | Examples | Placement |
| --- | --- | --- |
| Invariant | safety boundary, authorization rule, required contract | highest applicable persistent layer |
| Stable project fact | build command, repository boundary, naming convention | project instruction or concise linked reference |
| Conditional procedure | deployment steps, format-specific workflow, rare recovery | discoverable skill or reference loaded on trigger |
| Task input | issue details, requested artifact, current data | current request, near the dynamic work |
| Derived state | findings, decisions, completed steps | compact task checkpoint, not permanent memory by default |
| Ephemeral output | raw logs, search matches, generated traces | summarize or store as an artifact; do not replay wholesale |

Promote information to a more persistent layer only when its reuse value exceeds its recurring load and staleness risk.

## Optimize the routing layer first

Names and descriptions are often visible before a skill or tool is selected, so they are recurring costs.

- State the capability and activation boundary in concrete language.
- Include exclusions only when they prevent likely misrouting.
- Remove feature catalogs, marketing claims, examples, and procedures from descriptions.
- Avoid descriptions so broad that several skills activate for ordinary work. An explicitly universal skill must keep its loaded body exceptionally small and defer conditional detail.
- Put tool-specific behavior in the tool description when it applies only to that tool. Keep cross-tool policy in shared instructions.

Test routing with representative positive, negative, and ambiguous requests. Optimize for correct activation, not description length alone.

## Write outcome-first instructions

Prefer this information order when the runtime does not require another shape:

1. desired outcome;
2. success or completion evidence;
3. material constraints and authorization boundaries;
4. relevant context and available resources;
5. output shape;
6. fixed steps only where sequence is an actual invariant.

Remove instructions that merely restate the model's normal competence. Replace repeated prose with one precise rule. Use `always` and `never` only for genuine invariants; use decision criteria for judgment calls.

Preserve the user's chosen artifact, tone, length, and scope before improving style. Do not turn token optimization into terse, incomplete, or mechanical output.

## Use progressive disclosure

Keep the entry point sufficient for the common case. Move substantial conditional procedures, platform variants, schemas, templates, and examples into focused references. Every reference must be linked at the decision point that requires it.

Avoid chains of references that force several reads before work can start. Do not duplicate the same rule in the entry point and a reference. Delete placeholder resources and generic tutorials.

For skills, validate at least:

- exact folder and frontmatter name alignment;
- concise, discriminating discovery metadata;
- no unfinished placeholders or broken relative links;
- an explicit invocation policy only when the user requests one;
- representative behavior, not regex matches against headings;
- material rules retained after compression.

## Cache-aware prompt construction

When the API or runtime caches common prefixes, keep stable shared material in a consistent prefix and place dynamic user or task content afterward. Avoid injecting volatile timestamps, reordered lists, request IDs, or regenerated prose into the stable prefix unless the task needs them.

This is not universal prompt ordering. For long-document reasoning, follow the target model's current guidance; some models perform better with source documents before the query. Treat cache layout and reasoning layout as separate concerns and test both.

## Compress safely

Use semantic compression, not deletion by line count:

1. remove exact duplication;
2. remove obsolete or contradicted guidance;
3. replace repeated cases with a decision rule;
4. move conditional detail behind a trigger;
5. convert prose enumerations to compact mappings when that improves scanning;
6. keep examples only when they disambiguate behavior;
7. verify that required behavior still occurs on representative tasks.

Do not optimize an instruction set only against its current examples. Hold out realistic tasks and accept a revision only when it preserves or improves outcome quality while reducing measured burden.
