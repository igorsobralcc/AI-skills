---
name: caching-strategy
description: Design caching only when justified, including placement, keys, freshness, invalidation, concurrency, capacity, privacy, failure, and measurement.
---

# Caching Strategy

## Golden rules

- State the latency, load, availability, or cost problem the cache solves and define the authoritative source.
- Keys include every representation variant and security boundary. Define freshness, ownership, invalidation, eviction, and stampede protection.
- Measure user value, origin load, stale responses, and failure behavior rather than hit rate alone.
- Make conditional HTTP caching and local computation caching explicit before adding distributed infrastructure.

## Guardrails

- Do not cache authorization decisions or sensitive responses across principals without proven isolation.
- Avoid unbounded keys, cache-as-database designs, stale write paths, synchronized expiration, and failure amplification.
- Do not add caching before measuring a relevant bottleneck.
