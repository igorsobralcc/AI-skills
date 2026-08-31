---
name: help
description: Help users find an available skill for a fully described task, or ask focused questions to complete an underspecified request.
---

# Help

Help the user turn their request into the next useful skill invocation.

## Find the right skill

- Interpret the user's goal, deliverable, technology, and risk or quality concerns.
- Search the available skill catalog and the installed skill list when those are available. Match by the skill's stated purpose and activation conditions, not by its name alone.
- Recommend the smallest useful set of skills. Name the primary skill first and explain its fit in one sentence; mention complementary skills only when their triggers clearly apply.
- If no suitable skill exists, say so plainly. Do not invent a skill or imply one is available.

## Decide whether the request is complete

A request has sufficient context for a suggested prompt when it states a concrete outcome and contains the material context needed to act safely and accurately. This normally includes the relevant system, artifact, or domain and any constraints, inputs, or success criteria that would change the approach.

- When the request is complete, answer the question, give concise practical tips, and offer one ready-to-use suggested prompt for the recommended skill. Preserve the user's wording and do not add assumptions that materially change the task.
- When material context is missing, do not provide tips or a suggested prompt. Ask only the smallest set of focused clarification questions needed to establish the outcome, relevant context, and constraints.
- Treat the request as incomplete when different reasonable answers would lead to meaningfully different skills, prompts, or actions.

## Response shape

For a complete request, respond with: the recommended skill or skills, why they fit, brief tips, and a suggested invocation such as `/skill-name ...`.

For an incomplete request, briefly explain what is missing and ask the clarification questions. Do not choose a skill prematurely unless one is already unambiguous.

## Guardrails

- This skill advises and routes; it does not perform the work the selected skill would perform.
- Do not claim that a catalog entry is installed or invocable without checking the available skills or the relevant catalog.
- Keep questions and recommendations proportional to the request; avoid turning ordinary work into a broad discovery interview.
