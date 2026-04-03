# Analytic Rubric Maker Core Specification

This document is the canonical, vendor-neutral source of truth for this repository. Agent adapters may add runtime-specific packaging or discovery notes, but they must not change the workflow, output contract, or grading logic defined here.

## Purpose

Create a compact analytic 4-level rubric in the user's language based on:

- a learning outcome
- one or more criteria

Use four ordered performance levels:

- insufficient
- sufficient
- good
- excellent

## Canonical Sources

Use the sources in this order:

1. this file for workflow and output behavior
2. [../references/rubric-ontwerp.md](../references/rubric-ontwerp.md) for rubric design heuristics and descriptor quality
3. the runtime adapter only for agent-specific loading or packaging details

If an adapter conflicts with this file, this file wins.

## Runtime Assumptions

This repository is designed to be portable across agent runtimes.

- No external tools or OS-specific commands are required to execute the workflow.
- A runtime only needs to read Markdown files from this repository and produce text output.
- If a runtime cannot follow relative links automatically, load the referenced files manually.
- If a runtime cannot render Markdown tables reliably, fall back to a plain-text table while preserving the same columns, order, and meaning.

## Workflow

### 1. Determine the language

Follow the user's language in questions, headings, level labels, and rubric text.

### 2. Collect the required input

The workflow requires both:

- learning outcome
- criteria

Always ask for each missing part. Ask briefly and directly.

Use this logic:

- if both are missing: ask for the learning outcome and the criteria in one message
- if only the learning outcome is missing: ask only for the learning outcome
- if only the criteria are missing: ask only for the criteria

Accept criteria as bullets, sentences, fragments, or rough notes.

### 3. Rewrite the criteria

Rewrite each criterion into an observable and assessable criterion before writing level descriptors.

Apply these rules:

- make the criterion concrete enough to show observable behavior, product quality, or performance
- avoid vague container terms without a clear object, such as `professional`, `adequately developed`, or `good analysis`
- make implicit expectations explicit, such as justification, coherence, transfer, independence, or source use, but do not add a new content domain that is not implied by the input
- split compound criteria only when it is otherwise unclear what is being assessed
- phrase criteria briefly and directly

### 4. Anchor `good` to the criterion

Treat `good` as the target performance that matches the criterion itself. Derive the other levels from that anchor.

Use this logic:

- `good`: clearly meets the criterion
- `sufficient`: meets the criterion in broad terms, but with limits in quality, depth, coherence, independence, transfer, or precision
- `excellent`: exceeds `good` through relevant added value such as greater depth, stronger integration, better practical usefulness, stronger handling of complexity, more critical justification, broader perspective, or an original approach when appropriate
- `insufficient`: shows substantial shortcomings; parts are missing, incorrect, incoherent, or not demonstrable

### 5. Write short descriptors

Keep descriptors compact. Do not use empty intensifiers.

Write:

- yes: concrete quality differences
- no: ladders built only from words such as `somewhat`, `good`, `very good`, `reasonable`, or `weak`

Make differences visible through distinct quality features, not by labeling the same feature as slightly stronger or weaker.

### 6. Build the output

Present the rubric as a table.

Use this default structure:

1. name the learning outcome
2. optionally show a short list of rewritten criteria if that improves readability
3. provide the rubric as a table

Use these columns in this order:

| Criterion | Insufficient | Sufficient | Good | Excellent |
| --- | --- | --- | --- | --- |

Always localize the visible output to the user's language, including level labels, headings, and surrounding text.

### 7. Check the rubric

Check every criterion and every level before delivering.

Run at least these checks:

- is each criterion observable and assessable
- does `good` match the criterion in substance
- do the levels differ through performance quality rather than loose intensifiers
- are the descriptors short enough
- is `excellent` truly more than just more of the same
- is `insufficient` clearly below standard without merely saying `not good`
- is the visible output language consistent with the user's language

## Missing Input Prompt Rule

When input is missing, ask in the user's language. Keep the question short and direct.

The prompt must communicate that the rubric needs:

- the learning outcome
- the criteria

If only one of those is missing, ask only for that missing part.

## Output Contract

Every compliant runtime output must satisfy all of the following:

- the visible output is in the user's language
- the rubric uses exactly four ordered levels equivalent to `insufficient`, `sufficient`, `good`, and `excellent`
- `good` is anchored to the criterion itself
- the criteria are observable and assessable
- descriptors are short and concrete
- the structure is stable enough that different runtimes produce equivalent rubrics from the same input

## Non-Goals

This repository does not require:

- a graphical user interface
- a specific model vendor
- tool execution, shell access, or platform-specific automation
- long pedagogical explanations unless the user explicitly asks for them
