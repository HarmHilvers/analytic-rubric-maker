---
name: analytic-rubric-maker
description: Create an analytic 4-level rubric or assessment form with the levels insufficient, sufficient, good, and excellent based on a learning outcome and criteria. Use when the user asks for an assessment form, a rubric for a learning outcome, an analytic rubric, or a conversion of criteria into a 4-level rubric. Always ask for the learning outcome and criteria when they are missing, rewrite criteria so they are observable and assessable, keep descriptors short, and always follow the user's language in the final output.
---

# Analytic Rubric Maker for Codex

This file is the Codex/OpenAI skill adapter for this repository.

## Canonical Source

Read [core/spec.md](core/spec.md) first. That file is the canonical, vendor-neutral workflow and output contract.

Then read [references/rubric-ontwerp.md](references/rubric-ontwerp.md) for rubric design heuristics.

If this adapter conflicts with the core specification, the core specification wins.

## Adapter Role

Use this skill when the user asks for an analytic rubric, beoordelingsformulier, assessment form, or a conversion of criteria into a 4-level rubric.

In Codex, this file exists so the runtime can discover the repository as a skill. Keep runtime-specific behavior thin:

- follow the workflow from [core/spec.md](core/spec.md)
- preserve the output contract from [core/spec.md](core/spec.md)
- use [references/rubric-ontwerp.md](references/rubric-ontwerp.md) only as supporting guidance
- do not introduce Codex-specific output structure beyond what the core requires

## Codex Notes

When the user input is incomplete, ask for the missing part in the user's language and keep the question brief.

Keep the visible output practical and direct. Avoid extended pedagogical explanation unless the user explicitly asks for it.

Prefer a Markdown table when the runtime supports it.

If table rendering is weak in the current runtime, fall back to a plain-text table while preserving the same order and meaning as the core specification.
