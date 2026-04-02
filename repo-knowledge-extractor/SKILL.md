---
name: repo-knowledge-extractor
description: Use when turning repository observations into durable team knowledge, especially for legacy or poorly documented systems where the goal is to extract terminology, business rules, conventions, hidden constraints, pitfalls, and repeatable engineering guidance.
---

# Repo Knowledge Extractor

Convert scattered repo clues into maintainable team knowledge.

## Output Contract

Write these files into the target repo by default:

- `docs/repo-brief/repo-knowledge-base.md`
- `docs/repo-brief/pitfalls.md`
- `docs/repo-brief/engineering-conventions.md`

Use [references/knowledge-artifacts.md](references/knowledge-artifacts.md) for the default structure.

## What This Skill Extracts

- domain terms and aliases
- visible business rules
- hidden invariants
- codebase conventions
- common failure modes
- manual checks and release cautions

This is not a general summary. It is team memory captured from code and docs.

## Hard Rules

1. Separate explicit rule from inferred rule.
2. Prefer repeated evidence over one-off hints.
3. If a convention is weakly enforced, say so.
4. Record missing human knowledge instead of making it up.
5. Focus on what will prevent future mistakes, not on encyclopedic coverage.

## Workflow

### Phase 0: Scope

Decide whether the extraction is for:

- the whole repo
- one application or service
- one hotspot module

### Phase 1: Mine Evidence

Look in:

- README and docs
- tests and fixtures
- validation code and enums
- comments that explain edge cases
- CI, lint, build, and release scripts
- repeated patterns in filenames, directories, and APIs

Extract candidates for:

- terms
- business rules
- conventions
- pitfalls
- release or verification habits

### Phase 2: Consolidate and De-duplicate

Group findings into:

- explicit conventions
- implicit conventions
- hard invariants
- fragile areas
- open questions for humans

Reject findings that are too thinly evidenced.

### Phase 3: Write the Artifacts

Produce:

- `repo-knowledge-base.md`: durable team memory and domain rules
- `pitfalls.md`: common mistakes, high-risk areas, recovery clues
- `engineering-conventions.md`: naming, layering, testing, config, delivery conventions

## Review Checklist

- Are terms tied to code or docs evidence?
- Are inferred rules labelled as inferred?
- Are pitfalls concrete enough to change behavior?
- Are weak conventions distinguished from hard constraints?
- Are missing human answers listed explicitly?
