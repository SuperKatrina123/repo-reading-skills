---
name: repo-reading-system
description: Use when the user wants to understand an unfamiliar repository, take over a project, map architecture, find where to change code, or turn repository knowledge into reusable team documentation. This is the default entry skill for repo reading and should route to the right reading mode automatically.
---

# Repo Reading System

Use this as the default entry skill for repository understanding work.

Do not treat repo reading as one generic summary task. Route the request into the smallest useful mode, then load only the matching sub-skill(s).

## Available Modes

- `repo-onboarding`
  - first contact with a repo
  - newcomer handoff
  - reading order
  - first files to inspect
- `architecture-trace`
  - runtime understanding
  - boundaries, entrypoints, request flow, event flow, state transitions
- `change-entry-finder`
  - the change is already known
  - user needs entrypoints, blast radius, tests, risks
- `repo-knowledge-extractor`
  - durable team memory
  - terms, conventions, hidden rules, pitfalls

Read [references/mode-selection.md](references/mode-selection.md) before choosing the mode.

## Routing Rules

1. If the user is unfamiliar with the repo, start with `repo-onboarding`.
2. If the user asks how the system runs, how modules collaborate, or how data flows, add `architecture-trace`.
3. If the user already knows what they want to modify, switch to `change-entry-finder`.
4. If the user wants documentation that outlives the current session, add `repo-knowledge-extractor`.
5. If more than one mode applies, use the minimum useful chain instead of loading everything by default.

## Recommended Execution Order

Use this order when chaining modes:

1. `repo-onboarding`
2. `architecture-trace`
3. `change-entry-finder`
4. `repo-knowledge-extractor`

Skip steps that do not add value for the current request.

## Output Strategy

Default output root:

- `docs/repo-brief/`

When multiple modes are used:

- avoid duplicated sections
- keep terminology consistent across files
- reuse earlier evidence instead of rescanning blindly
- preserve a clear split between `Facts`, `Inferences`, and `Unknowns`

## Hard Rules

1. Never invent architecture, business rules, or production behavior.
2. Prefer evidence-backed file paths and commands over prose.
3. If the repo is large, narrow to the requested app, service, or module first.
4. Choose the smallest artifact set that answers the user’s decision.
5. If ambiguity remains, record it explicitly instead of expanding scope.

## Handoff

At the start of repo-reading work:

- state which mode you selected
- state which additional sub-skill(s) you will load, if any
- state the expected artifacts

Typical examples:

- "Using `repo-reading-system` -> `repo-onboarding` for a first-pass repo brief."
- "Using `repo-reading-system` -> `repo-onboarding` + `architecture-trace` to build onboarding docs plus runtime flow."
- "Using `repo-reading-system` -> `change-entry-finder` because the requested change is already specific."
