# Repo Knowledge Extractor

This sub-skill is for turning repository observations into durable team knowledge.

It is not aimed at one-time explanation. It extracts long-lived value from code, docs, tests, and scripts: terms, rules, conventions, hidden constraints, and common pitfalls.

## When To Use

Use it for questions like:

- How do we build a knowledge base for this legacy project?
- What conventions does the team rely on but rarely document?
- Which parts of the repo are risky or easy to misuse?
- What testing, config, or release habits should be recorded?

If the task is simply first-time repo onboarding, start with `repo-onboarding`.  
If the goal is to locate a concrete code change, use `change-entry-finder` instead.

## Default Outputs

Default output root:

```text
docs/repo-brief/
```

Fixed artifacts:

- `repo-knowledge-base.md`
- `pitfalls.md`
- `engineering-conventions.md`

## What This Skill Does

- extract domain terms and aliases
- identify explicit and implicit business rules
- document engineering conventions visible in the codebase
- summarize high-risk areas and common mistakes
- turn repo-visible but under-documented knowledge into durable docs

## Example Prompts

```text
Use repo-knowledge-extractor to build a knowledge base for this legacy project.
```

```text
Use repo-knowledge-extractor to extract terms, conventions, and pitfalls from this repository.
```

```text
Use repo-knowledge-extractor to output a knowledge base, pitfalls, and conventions.
```

## Relationship To Other Skills

- often serves as the documentation step under `repo-reading-system`
- can follow `repo-onboarding` or `architecture-trace`
- does not locate exact edit paths; that is handled by `change-entry-finder`

## File Structure

```text
repo-knowledge-extractor/
├── README.md
├── README-ZH.md
├── README-EN.md
├── SKILL.md
└── references/
    └── knowledge-artifacts.md
```
