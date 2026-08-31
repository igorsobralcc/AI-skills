---
name: debugging-workflow
description: Diagnose bugs, regressions, intermittent failures, and unexplained behavior through reproduction, evidence, hypothesis testing, root cause, and regression planning.
---

# Debugging Workflow

Use during bug refinement before `change-planning` writes the specification.

## Golden rules

- Capture expected and actual behavior, environment, inputs, timeline, frequency, affected versions or data, and the smallest reliable reproduction.
- Form falsifiable hypotheses and change one variable at a time using the least-invasive evidence first.
- Distinguish root cause, trigger, contributing conditions, and symptoms.
- Add the reproduction and regression scenario to acceptance criteria and the testing strategy.

## Guardrails

- Diagnosis does not authorize implementing the fix, altering production state, or running destructive experiments.
- Protect secrets and customer data; bound logs, queries, and profiling.
- Do not conclude from correlation or stop at a workaround when root cause remains relevant.
