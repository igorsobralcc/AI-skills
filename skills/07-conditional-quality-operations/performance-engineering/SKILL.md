---
name: performance-engineering
description: Define and verify performance budgets, workloads, benchmarks, profiling, capacity, and optimizations when explicit requirements or evidence justify it.
---

# Performance Engineering

Activate for latency, throughput, concurrency, large-data, capacity, resource, or cost requirements, or an evidenced performance problem.

## Golden rules

- Define user-visible budgets and a representative workload, dataset, concurrency model, environment, and baseline.
- Measure latency distributions, throughput, errors, saturation, and resource cost; profile before optimizing.
- Optimize the dominant constraint, preserve behavior, and remeasure under the same conditions.
- Add regression budgets or tests where stable measurement is feasible.

## Guardrails

- Do not optimize from intuition, trade correctness or accessibility for scores, or extrapolate from debug builds and tiny microbenchmarks.
- Control benchmark noise and disclose uncertainty.
- Production load tests and invasive profiling require authorization and abort conditions.
