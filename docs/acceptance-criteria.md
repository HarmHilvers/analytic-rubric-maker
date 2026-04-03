# Acceptance Criteria and Regression Criteria

Use this document to verify that the repository remains compatible across agents after edits.

## Acceptance Criteria

The repository is acceptable only if all of the following are true:

- the canonical workflow lives in [../core/spec.md](../core/spec.md)
- agent-specific entry points are adapters that reference the core specification instead of redefining it
- Codex/OpenAI support still exists after the refactor
- Claude support exists through a dedicated adapter
- generic non-vendor support exists through a dedicated adapter
- the reference design guidance remains available and is still compatible with the core specification
- the README explains how the repository is used per runtime
- portability limits and fallbacks are documented without introducing hard OS or tool dependencies
- the output contract is explicit enough that different runtimes are expected to produce materially consistent rubrics from the same input

## Behavioral Regression Criteria

An edit is a regression if it causes any of the following:

- missing required input is no longer requested explicitly
- visible output no longer follows the user's language
- the rubric no longer uses exactly four ordered levels equivalent to `insufficient`, `sufficient`, `good`, and `excellent`
- `good` is no longer anchored to the criterion itself
- criteria are left vague when they should be rewritten into observable and assessable criteria
- descriptors drift into long prose or vague intensifier ladders
- `excellent` becomes a generic superlative without clear added value
- `insufficient` is described only as the negation of a higher level
- runtime adapters diverge in core logic or grading semantics

## Adapter Regression Criteria

An adapter change is a regression if it:

- duplicates large parts of the core workflow without need
- introduces vendor-specific rubric rules
- stops pointing to the canonical core files
- omits fallbacks for runtimes that cannot follow links or render Markdown tables

## README Regression Criteria

README changes are a regression if they:

- describe only one runtime as if it were canonical
- fail to explain the runtime model and repository structure
- omit setup or use guidance for Codex/OpenAI, Claude, or other agents
- introduce usage examples that are not required for understanding the runtime model
