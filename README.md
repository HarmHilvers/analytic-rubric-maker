# analytic-rubric-maker

Create a compact analytic 4-level rubric based on a learning outcome and criteria.

## What it does

This skill turns a learning outcome and one or more criteria into an analytic rubric with four levels:

- Insufficient
- Sufficient
- Good
- Excellent

It is intended for requests such as:

- making an assessment form
- creating an analytic rubric
- converting rough criteria into a 4-level rubric
- rewriting vague criteria into observable, assessable criteria

## Installation

This repository is structured as a Codex skill: a folder with a `SKILL.md` file and optional supporting files. Codex discovers skills either from your global Codex home directory or from a project-local skills folder.

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

## Input

This skill needs two things:

- a learning outcome
- the criteria

Criteria may be given as bullets, notes, rough phrases, or sentences.

## Output

The default output is a markdown table with this structure:

| Criterion | Insufficient | Sufficient | Good | Excellent |
| --- | --- | --- | --- | --- |

The visible output is always written in the user’s language.

## Design principles

- Rewrite criteria so they are observable and assessable.
- Keep descriptors short and concrete.
- Anchor **good** to the criterion itself.
- Make level differences visible through quality features, not vague intensifiers.
- Use **excellent** for relevant added value, not just “more of the same”.
- Make **insufficient** clearly below standard.

## Workflow

1. Determine the user’s language.
2. Check whether both the learning outcome and criteria are present.
3. Rewrite the criteria where needed.
4. Build four performance levels.
5. Present the rubric as a compact markdown table.
6. Check clarity, observability, and consistency.

## Repository structure

- `SKILL.md` — skill instructions and rubric workflow
- `references/rubric-ontwerp.md` — rubric design guidance
