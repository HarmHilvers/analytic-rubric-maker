# analytic-rubric-maker

Create a compact analytic 4-level rubric based on a learning outcome and criteria.

## Runtime Model

This repository is multi-agent by design.

- [`core/spec.md`](core/spec.md) is the canonical, vendor-neutral source of truth
- [`references/rubric-ontwerp.md`](references/rubric-ontwerp.md) provides rubric design heuristics used by every runtime
- `agents/` contains thin runtime adapters
- [`SKILL.md`](SKILL.md) remains the Codex skill entry point and acts as the Codex/OpenAI adapter

Adapters are not allowed to redefine the workflow. They only package the same core behavior for a specific runtime.

## What It Does

The repository turns a learning outcome and one or more criteria into an analytic rubric with four levels:

- Insufficient
- Sufficient
- Good
- Excellent

## Installation

Clone the repository into the location your runtime expects. The same repository contents are shared across runtimes.

```bash
git clone https://github.com/HarmHilvers/analytic-rubric-maker.git
```

## Use with Codex / OpenAI

Codex support is preserved through [`SKILL.md`](SKILL.md) and [`agents/openai.yaml`](agents/openai.yaml).

- For Codex skill discovery, install the repository as a skill folder containing `SKILL.md`.
- For OpenAI-oriented wrappers that use agent metadata, use `agents/openai.yaml` as the runtime-facing adapter.
- In both cases, the runtime should treat [`core/spec.md`](core/spec.md) as canonical and [`references/rubric-ontwerp.md`](references/rubric-ontwerp.md) as supporting guidance.

### Option 1: install globally

```bash
git clone https://github.com/HarmHilvers/analytic-rubric-maker.git ~/.codex/skills/analytic-rubric-maker
```

### Option 2: install in a project

```bash
mkdir -p .agents/skills
git clone https://github.com/HarmHilvers/analytic-rubric-maker.git .agents/skills/analytic-rubric-maker
```

After installation, restart Codex or start a new session so the skill can be discovered.

## Use with Claude

Claude support is provided through [`agents/claude.md`](agents/claude.md).

- Use `agents/claude.md` as the Claude-facing entry point.
- Load the files in the order documented there.
- Keep the adapter thin and preserve the workflow and output contract from [`core/spec.md`](core/spec.md).

## Use with Other Agents

Generic support is provided through [`agents/generic.md`](agents/generic.md).

- Use that file when the host framework does not natively support Codex skills or the OpenAI adapter format.
- Preload linked files manually if the framework cannot follow repository links.
- If Markdown table rendering is weak, preserve the same output structure in plain text.

## Input

The workflow needs two things:

- a learning outcome
- the criteria

Criteria may be given as bullets, notes, rough phrases, or sentences.

## Output

The default output is a markdown table with this structure:

| Criterion | Insufficient | Sufficient | Good | Excellent |
| --- | --- | --- | --- | --- |

The visible output is always written in the user's language.

## Design principles

- Rewrite criteria so they are observable and assessable.
- Keep descriptors short and concrete.
- Anchor **good** to the criterion itself.
- Make level differences visible through quality features, not vague intensifiers.
- Use **excellent** for relevant added value, not just "more of the same".
- Make **insufficient** clearly below standard.

## Compatibility Documents

- [`docs/compatibility-contract.md`](docs/compatibility-contract.md) defines the cross-agent compatibility contract
- [`docs/acceptance-criteria.md`](docs/acceptance-criteria.md) defines acceptance and regression criteria

## Repository structure

- `core/spec.md` — canonical vendor-neutral workflow and output contract
- `SKILL.md` — Codex skill adapter
- `agents/openai.yaml` — OpenAI adapter metadata
- `agents/claude.md` — Claude adapter
- `agents/generic.md` — generic adapter for other runtimes
- `references/rubric-ontwerp.md` — rubric design guidance
- `docs/compatibility-contract.md` — cross-agent compatibility contract
- `docs/acceptance-criteria.md` — acceptance and regression criteria
