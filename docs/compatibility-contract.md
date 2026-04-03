# Cross-Agent Compatibility Contract

This document defines the explicit compatibility contract for any runtime that uses this repository.

## Scope

The contract applies to:

- Codex and other OpenAI runtimes
- Claude-based runtimes
- other agent frameworks that can load repository files and generate text output

## Canonical Hierarchy

The repository must be interpreted in this order:

1. [../core/spec.md](../core/spec.md)
2. [../references/rubric-ontwerp.md](../references/rubric-ontwerp.md)
3. runtime adapters in `agents/`

Adapters may package or route instructions for a runtime, but they must not override the workflow or output contract in the core specification.

## Required Runtime Capabilities

A compatible runtime must be able to:

- read the relevant repository files, directly or through preloaded context
- ask for missing user input
- produce plain text output

Markdown table support is preferred but not required.

## Required Behavioral Guarantees

Every compatible runtime must:

- ask for missing required input instead of silently inventing it
- treat the user's language as the visible output language
- preserve the four ordered rubric levels equivalent to `insufficient`, `sufficient`, `good`, and `excellent`
- anchor `good` to the criterion itself
- rewrite criteria into observable and assessable criteria before writing descriptors
- keep descriptors short and concrete
- distinguish levels by quality features rather than loose intensifiers
- keep `excellent` as relevant added value, not just more of the same
- keep `insufficient` clearly below standard

## Adapter Contract

Each adapter in `agents/` or other runtime-specific entry points must:

- reference the core specification as canonical
- stay thin and avoid duplicating the full core workflow unless runtime constraints require it
- avoid vendor-specific grading rules or level semantics
- describe portability limits and fallbacks when the runtime cannot follow links or render Markdown tables

## Portability Rules

- Do not require shell commands, platform-specific tooling, or operating-system-specific automation to execute the rubric workflow.
- If a runtime cannot follow relative file references, the integrator must preload the referenced files in canonical order.
- If a runtime cannot render Markdown tables, it must preserve the same column order and meaning in an equivalent plain-text format.

## Invariants

These points are invariant across agents:

- same required inputs
- same criterion rewriting standard
- same four-level semantics
- same preference for compact output
- same language-following behavior

## Non-Compliant Changes

The following changes break compatibility:

- changing the meaning or order of the four levels
- moving canonical workflow logic out of the core specification and into an adapter
- making one vendor's adapter the de facto source of truth
- requiring runtime-specific tooling to perform the basic workflow
- changing output behavior in a way that makes two compliant runtimes produce materially different rubric logic from the same input
