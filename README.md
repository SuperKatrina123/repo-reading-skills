# Repo Reading Skills

A collection of GitHub Copilot skills for systematically understanding unfamiliar repositories.

Instead of one generic "summarize this repo" prompt, this system routes each request into a focused mode and produces reusable, structured outputs.

## Skills

[`repo-reading-system`](./repo-reading-system/) is the main entry skill. It detects intent and routes to the right sub-skill(s). Sub-skills live inside it:

| Sub-skill | Purpose |
|---|---|
| [`repo-onboarding`](./repo-reading-system/repo-onboarding/) | First pass on an unfamiliar repo: overview, reading path, glossary |
| [`architecture-trace`](./repo-reading-system/architecture-trace/) | Runtime understanding: entrypoints, module flow, data flow, state changes |
| [`change-entry-finder`](./repo-reading-system/change-entry-finder/) | Locate where to change code, blast radius, test surface, and risks |
| [`repo-knowledge-extractor`](./repo-reading-system/repo-knowledge-extractor/) | Extract durable team docs: conventions, terms, hidden rules, pitfalls |

## Quick Start

In most cases, trigger the entry skill and let it route automatically:

```text
Use repo-reading-system to help me take over this repository quickly.
```

```text
Use repo-reading-system to explain the runtime architecture of this project.
```

```text
Use repo-reading-system to find where I should modify code to add one API field.
```

```text
Use repo-reading-system to turn this legacy project into a reusable team brief.
```

## Default Outputs

All skills write under `docs/repo-brief/` by default. Typical artifacts:

```
docs/repo-brief/
├── repo-overview.md
├── reading-path.md
├── glossary.md
├── architecture-map.md
├── module-dependency-map.md
├── runtime-flow.md
├── repo-knowledge-base.md
├── pitfalls.md
├── engineering-conventions.md
└── changes/
    └── <topic>/
        ├── change-impact-report.md
        ├── entrypoints.md
        └── test-surface.md
```

## Routing Logic

```
repo-reading-system
├── unfamiliar repo?           → repo-onboarding
├── need runtime understanding? → architecture-trace
├── change is already known?   → change-entry-finder
└── want durable team docs?    → repo-knowledge-extractor
```

Use the smallest chain that answers the current question. Skip steps that add no value.

## Installation

These skills are plain markdown files and work with any AI coding assistant that supports custom instructions or skill loading.

### GitHub Copilot

Copy the skill folders into your project and reference them in `.github/copilot-instructions.md`:

```md
Use the skills in `.github/skills/repo-reading-system/` for all repo reading tasks.
```

Or add them to your Copilot workspace `.yml` config under `skills:`.

### Claude Code

Copy the skill folders into your project, then add a reference in `CLAUDE.md`:

```md
## Skills
For repo reading and understanding tasks, load the skill from `skills/repo-reading-system/SKILL.md`.
```

Or paste the `SKILL.md` content directly into `CLAUDE.md` if you only need one skill.

### Codex (OpenAI)

Copy the skill folders into your project, then reference them in `AGENTS.md`:

```md
## Skills
For repo reading tasks, follow the instructions in `skills/repo-reading-system/SKILL.md`.
```

### General

Any tool that accepts a system prompt or custom instructions file can use these skills — just paste the contents of `SKILL.md` into your instruction file.
