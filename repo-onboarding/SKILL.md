---
name: repo-onboarding
description: Use when first taking over an unfamiliar code repository, helping a new engineer understand a project quickly, or needing a structured repo brief with purpose, stack, startup flow, core modules, reading order, and first files to inspect.
---

# Repo Onboarding

Turn a repository into a practical newcomer brief instead of an ad hoc summary.

## Output Contract

Write these files into the target repo by default:

- `docs/repo-brief/repo-overview.md`
- `docs/repo-brief/reading-path.md`
- `docs/repo-brief/glossary.md`

If the user gives a different output path, follow it.

Use [references/repo-brief-structure.md](references/repo-brief-structure.md) for the default headings.

## What Good Looks Like

By the end of this skill, a newcomer should be able to answer:

- What does this repo do?
- How do I run or test it locally?
- Which directories matter in week one?
- Which files are the true entrypoints?
- In what order should I read the code?
- Which terms or abbreviations will otherwise slow me down?

## When Not To Use

- If the user already knows the repo and needs runtime flow analysis, use `architecture-trace`.
- If the user already knows the change they want to make, use `change-entry-finder`.
- If the user wants long-lived team conventions and hidden rules extracted, use `repo-knowledge-extractor`.

## Hard Rules

1. Separate `Facts`, `Inferences`, and `Unknowns`.
2. Cite concrete file paths for major claims.
3. Never invent secrets, env values, owners, dashboards, or deployment details.
4. Curate the repo tree. Do not dump the full file list.
5. Prefer the smallest reading path that gets a newcomer productive.

## Workflow

### Phase 0: Scope

Establish:

- target path
- monorepo slice, if applicable
- runnable constraints in the current environment
- whether the user wants repo-level output or app/module-level output

### Phase 1: Evidence Scan

Prioritize:

- `README*`, `docs/`, existing architecture notes
- manifests and build files
- app/server entrypoints
- routing tables, config, env examples
- test commands and CI files
- top-level directories that define module boundaries

Extract:

- repo purpose in plain language
- tech stack
- startup/build/test commands
- key directories and responsibilities
- candidate entrypoint files
- 5-10 files a newcomer should read first
- project-specific terms worth defining

### Phase 2: Build the Reading Path

Convert the scan into an explicit path:

- first look: orientation files
- second look: runtime entrypoints
- third look: one core flow
- fourth look: supporting modules and tests

For every step, explain:

- what question this step answers
- which files to read
- what can be safely skipped for now

### Phase 3: Write the Artifacts

Produce:

- `repo-overview.md`: purpose, stack, startup, module map, first files
- `reading-path.md`: step-by-step reading sequence with intent per step
- `glossary.md`: repo terms, aliases, acronyms, and code-language translations

### Phase 4: Sanity Check

Verify:

- each artifact is evidence-backed
- entrypoints are concrete, not guessed
- the reading path is actionable for someone with near-zero context
- unknowns are explicit instead of papered over

## Preferred Style

- Short sections
- Checklists and tables where useful
- Plain language first, code terms second
- One-week onboarding usefulness over completeness
