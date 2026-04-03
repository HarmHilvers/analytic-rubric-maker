# Generic Agent Adapter

This adapter is for other agent frameworks that can load repository files but do not use the Codex skill format or the OpenAI adapter format.

## Canonical Load Order

Read these files in this order:

1. [../core/spec.md](../core/spec.md)
2. [../references/rubric-ontwerp.md](../references/rubric-ontwerp.md)
3. this adapter only for generic runtime notes

If this adapter conflicts with the core specification, the core specification wins.

## Adapter Duties

- treat [../core/spec.md](../core/spec.md) as the sole canonical workflow
- preserve the output contract and four-level rubric semantics across runtimes
- keep runtime integration thin and avoid introducing framework-specific rubric behavior
- keep visible output in the user's language

## Runtime Notes

- if the host runtime has a notion of system prompt, project memory, or task instructions, load this adapter there
- if the host runtime cannot read linked files automatically, inline or preload the core specification and reference document
- if the host runtime does not support Markdown tables, emit an equivalent plain-text table without changing column order or level meaning
