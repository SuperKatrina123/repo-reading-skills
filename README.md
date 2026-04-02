# Repo Reading Skills

A collection of GitHub Copilot skills for systematically understanding unfamiliar repositories.

Instead of one generic "summarize this repo" prompt, this system routes each request into a focused mode and produces reusable, structured outputs.

## Skills

| Skill | Purpose |
|---|---|
| [`repo-reading-system`](./repo-reading-system/) | Entry skill — detects intent and routes to the right sub-skill(s) |
| [`repo-onboarding`](./repo-onboarding/) | First pass on an unfamiliar repo: overview, reading path, glossary |
| [`architecture-trace`](./architecture-trace/) | Runtime understanding: entrypoints, module flow, data flow, state changes |
| [`change-entry-finder`](./change-entry-finder/) | Locate where to change code, blast radius, test surface, and risks |
| [`repo-knowledge-extractor`](./repo-knowledge-extractor/) | Extract durable team docs: conventions, terms, hidden rules, pitfalls |

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

Copy any skill folder into your project's `.github/copilot/skills/` directory, or reference it directly in your Copilot workspace configuration.
