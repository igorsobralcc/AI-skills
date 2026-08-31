---
name: cli-design
description: Design or review command-line interfaces, commands, flags, input, output, errors, configuration, exit codes, help, and scripting compatibility.
---

# CLI Design

## Golden rules

- Use predictable verbs and nouns, stable exit codes, actionable errors, discoverable help, and explicit precedence among flags, environment, and config.
- Write results to stdout and diagnostics to stderr; offer machine-readable output when automation is a supported use case.
- Make noninteractive behavior deterministic and provide dry-run for meaningful mutations.
- Preserve compatibility or document and stage breaking command changes.

## Guardrails

- Do not prompt in automation unexpectedly, expose secrets in arguments or output, or perform destructive work from ambiguous defaults.
- Require explicit confirmation interactively and an explicit force or approval flag noninteractively.
- Do not add subcommands or configuration layers without a real use case.
