---
name: change-entry-finder
description: Use when the desired change is already known and the user needs exact entrypoints, affected modules, likely call chains, linked edits, test locations, and risk analysis before modifying code.
---

# Change Entry Finder

Turn "where should I change this?" into a repeatable impact analysis.

## Output Contract

Write outputs under a topic folder by default:

- `docs/repo-brief/changes/<topic>/change-impact-report.md`
- `docs/repo-brief/changes/<topic>/entrypoints.md`
- `docs/repo-brief/changes/<topic>/test-surface.md`

If the user does not provide `<topic>`, derive a short slug from the requested change.

Use [references/change-artifacts.md](references/change-artifacts.md) for default headings.

## Input Expectation

Start from one explicit change statement, for example:

- add one API field
- adjust a form validation rule
- change a payment state transition
- add one analytics event

If the request is vague, narrow it before scanning.

## Hard Rules

1. Trace from a concrete entrypoint, not from a guessed module.
2. List both direct edits and likely linked edits.
3. Separate "must change" from "verify only".
4. Include tests, fixtures, snapshots, schema files, and config if relevant.
5. Mark hidden blast radius: shared types, state machines, serializers, tracking contracts.

## Workflow

### Phase 0: Normalize the Change

Write the change in one sentence:

- desired behavior
- affected entity or screen or API
- expected output shape
- obvious non-goals

### Phase 1: Find Entry Candidates

Search for:

- route / screen / handler / event consumer
- field name, validation rule, enum, status name
- API contract or DTO
- existing tests mentioning the same behavior

Output the best entrypoints first, with weaker candidates marked clearly.

### Phase 2: Walk the Impact Chain

For each likely entrypoint, inspect:

- controller / page / handler
- service / use case
- domain rules
- persistence / network contract
- shared types / schemas / serializers
- analytics / tracking / logs

Classify files as:

- must change
- likely linked change
- verify only

### Phase 3: Map Test Surface

Identify:

- unit tests
- integration tests
- end-to-end tests
- snapshots / fixtures / mocks
- missing test coverage

### Phase 4: Write the Artifacts

Produce:

- `change-impact-report.md`: summary, impact chain, risks, assumptions
- `entrypoints.md`: ranked file list and why each matters
- `test-surface.md`: what to run, what to add, and what is currently weak

## Review Checklist

- Is there at least one concrete entry file?
- Are downstream contracts covered?
- Are schema and test updates considered?
- Are risks tied to actual coupling points?
- Is uncertain impact marked as uncertain?
