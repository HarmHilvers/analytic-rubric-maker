# Claude Adapter

This adapter packages the repository for Claude-based runtimes.

## Canonical Load Order

Read these files in this order:

1. [../core/spec.md](../core/spec.md)
2. [../references/rubric-ontwerp.md](../references/rubric-ontwerp.md)
3. this adapter only for Claude-specific runtime notes

If this adapter conflicts with the core specification, the core specification wins.

## Adapter Duties

- keep the core workflow agent-neutral and unchanged
- preserve the four-level rubric structure and output contract from the core specification
- keep visible output in the user's language
- keep the adapter thin and avoid adding Claude-specific grading logic

## Runtime Notes

- if the Claude runtime supports project instructions, register this repository and point the runtime to this file as the entry point
- if the runtime cannot resolve relative links automatically, load the core and reference files manually
- if Markdown tables render poorly, emit a plain-text table with the same columns and ordering required by the core specification
