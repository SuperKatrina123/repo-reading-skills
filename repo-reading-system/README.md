# Repo Reading System

This is the main entry skill for repository reading work: understanding an unfamiliar repo, taking over a project, finding change entrypoints, and turning repo knowledge into reusable team documentation.

Instead of packing every repo-reading task into one giant prompt, this skill acts as a router:

- detect what the user actually needs
- load only the right sub-skill(s)
- keep outputs aligned under `docs/repo-brief/`

The goal is to turn “summarize this repo” into a reusable repo-understanding system.

## Included Modes

This skill routes into four focused sub-skills:

- `repo-onboarding`
  - first contact with a repository
  - build high-level understanding
  - produce a reading path and glossary
- `architecture-trace`
  - understand how the system actually runs
  - identify entrypoints, boundaries, module collaboration, data flow, and state changes
- `change-entry-finder`
  - the desired change is already known
  - locate entry files, blast radius, test surface, and risks
- `repo-knowledge-extractor`
  - turn repo knowledge into durable documentation
  - extract terms, conventions, hidden rules, and pitfalls

## Recommended Usage

In most cases, trigger the main skill directly instead of naming a sub-skill by hand:

```text
Use repo-reading-system to help me take over this repository quickly.
```

```text
Use repo-reading-system to explain the runtime architecture of this project.
```

```text
Use repo-reading-system to analyze where to modify code for “adding one API field”.
```

```text
Use repo-reading-system to turn this legacy project into a repo brief package.
```

## Routing Behavior

The default behavior is to choose the smallest useful mode:

- start with `repo-onboarding` when the repo is unfamiliar
- add `architecture-trace` when runtime understanding matters
- switch to `change-entry-finder` when the requested change is already specific
- add `repo-knowledge-extractor` when the user wants durable docs

If more than one mode applies, the skill should choose the smallest useful chain instead of loading everything by default.

## Default Outputs

Default output root:

```text
docs/repo-brief/
```

Typical artifacts include:

- `repo-overview.md`
- `reading-path.md`
- `glossary.md`
- `architecture-map.md`
- `module-dependency-map.md`
- `runtime-flow.md`
- `repo-knowledge-base.md`
- `pitfalls.md`
- `engineering-conventions.md`
- `changes/<topic>/change-impact-report.md`
- `changes/<topic>/entrypoints.md`
- `changes/<topic>/test-surface.md`

## Why This Exists

Many “summarize this repo” requests only produce a one-time explanation that cannot be reused or maintained.

This skill is designed to produce three stable kinds of outputs:

- understanding artifacts: help someone grasp the repo quickly
- action artifacts: show what to read, where to edit, and what to test
- durable artifacts: reduce the need to rediscover context next time

## File Structure

```text
repo-reading-system/
├── README.md
├── README-ZH.md
├── README-EN.md
├── SKILL.md
└── references/
    └── mode-selection.md
```
