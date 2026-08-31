---
name: local-development-experience
description: Improve clone-to-change setup, local services, configuration, debugging, test data, feedback loops, and troubleshooting without hiding production differences.
---

# Local Development Experience

## Golden rules

- Provide one documented, reproducible bootstrap path with versioned tools and clear prerequisites.
- Optimize time to first verified change and everyday edit-test-debug loops.
- Use safe synthetic data and local secret mechanisms; make service health and common failures understandable.
- Seek behavioral parity with production without reproducing unnecessary infrastructure.

## Guardrails

- Never bundle production credentials or customer data, require destructive reset by default, or silently modify global developer settings.
- Do not require containers or cloud environments when a simpler supported path works.
- Keep platform-specific limitations and alternatives explicit.
