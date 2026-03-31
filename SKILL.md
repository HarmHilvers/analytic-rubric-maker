---
name: analytic-rubric-maker
description: Create an analytic 4-level rubric or assessment form with the levels insufficient, sufficient, good, and excellent based on a learning outcome and criteria. Use when the user asks for an assessment form, a rubric for a learning outcome, an analytic rubric, or wants criteria converted into a 4-level rubric, for example with prompts such as "Maak een beoordelingsformulier voor deze leeruitkomst", "Maak een rubric voor deze leeruitkomst", "Maak een analytische rubric", or "Zet deze criteria om in een 4-punts rubric". Always ask for the learning outcome and criteria when they are missing, rewrite criteria so they are observable and assessable, keep descriptors short, and always follow the user's language in the final output.
---

# Analytic Rubric Maker

## Overview

Create an analytic rubric in the user's language. Use a compact table with criteria on the rows and the levels `insufficient`, `sufficient`, `good`, and `excellent` on the columns.

Read [references/rubric-ontwerp.md](references/rubric-ontwerp.md) first. Use those guidelines for rewriting criteria and defining level differences.

## Workflow

### 1. Determine the language

Follow the user's language in questions, headings, and rubric text.

### 2. Collect the required input

Check whether both inputs are present:

- learning outcome
- criteria

Always ask for each missing part. Ask briefly and directly.

Use this approach:

- If both are missing: ask for the learning outcome and the criteria in one message.
- If only the learning outcome is missing: ask only for the learning outcome.
- If only the criteria are missing: ask only for the criteria.

Accept criteria as bullets, sentences, fragments, or rough notes.

### 3. Rewrite the criteria

Rewrite each criterion into an observable and assessable criterion before writing level descriptors.

Apply these rules:

- Make the criterion concrete enough to show observable behavior, product quality, or performance.
- Avoid vague container terms without a clear object, such as `professional`, `adequately developed`, or `good analysis`.
- Make implicit expectations explicit, such as justification, coherence, transfer, independence, or source use, but do not add a new content domain that is not implied by the input.
- Split compound criteria only when it is otherwise unclear what is being assessed.
- Phrase criteria briefly and directly.

### 4. Anchor `good` to the criterion

Let `good` roughly match the criterion itself. Treat `good` as the target performance from which the other levels are derived.

Use this logic:

- `good`: clearly meets the criterion
- `sufficient`: meets the criterion in broad terms, but with limits in quality, depth, coherence, independence, transfer, or precision
- `excellent`: exceeds `good` through relevant added value such as greater depth, stronger integration, better practical usefulness, stronger handling of complexity, more critical justification, broader perspective, or an original approach
- `insufficient`: shows substantial shortcomings; parts are missing, incorrect, incoherent, or not demonstrable

### 5. Write short descriptors

Keep descriptors compact. Do not use empty intensifiers.

Write:

- yes: concrete quality differences
- no: ladders built only from words such as `somewhat`, `good`, `very good`, `reasonable`, or `weak`

Make differences visible through distinct quality features, not by labeling the same feature as slightly stronger or weaker.

### 6. Build the output

Present the rubric as a markdown table.

Use this default structure:

1. name the learning outcome
2. optionally show a short list of rewritten criteria if that helps
3. provide the rubric as a table

Use these columns:

| Criterion | Insufficient | Sufficient | Good | Excellent |
| --- | --- | --- | --- | --- |

Important: always localize the visible output to the user's language, including the level labels, headings, and any surrounding text.

### 7. Check the rubric

Check every criterion and every level before delivering.

Run at least these checks:

- Is each criterion observable and assessable?
- Does `good` match the criterion in substance?
- Do the levels differ through performance quality rather than loose intensifiers?
- Are the descriptors short enough?
- Is `excellent` truly more than just more of the same?
- Is `insufficient` clearly below standard without merely saying `not good`?
- Is the visible output language consistent with the user's language?

## Questions For Missing Input

When input is missing, use a short prompt adapted to the user's language in this form:

`The rubric needs two things: the learning outcome and the criteria. Send both, and I will turn them into a 4-level analytic rubric.`

## Output Style

Keep the output practical and direct. Avoid extended pedagogical explanation unless the user explicitly asks for it.
