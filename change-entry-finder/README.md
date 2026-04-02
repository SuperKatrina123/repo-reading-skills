# Change Entry Finder

This sub-skill is for the case where the desired change is already known, but the edit path is not.

Its job is not to explain the entire repository. Its job is to locate entry files, the impact chain, the test surface, and the main risks around one concrete change.

## When To Use

Use it for questions like:

- Where should I edit to add one API field?
- What else is affected by adjusting one form validation rule?
- Which modules are linked to a state-transition change?
- Which layers do I need to touch for a new analytics event?

The prerequisite is that the requested change is reasonably specific.  
If the repo is still completely unfamiliar, add `repo-onboarding` first.

## Default Outputs

Default output root:

```text
docs/repo-brief/changes/<topic>/
```

Fixed artifacts:

- `change-impact-report.md`
- `entrypoints.md`
- `test-surface.md`

## What This Skill Does

- normalize the requested change into one clear statement
- find likely entry files and downstream call chains
- separate must-change files from verify-only files
- include tests, fixtures, schemas, and linked risk points
- describe the blast radius instead of naming only one file

## Example Prompts

```text
Use change-entry-finder to analyze where to edit for “adding one API field”.
```

```text
Use change-entry-finder to map the impact of “changing a payment state transition”.
```

```text
Use change-entry-finder to output entrypoints, an impact report, and a test surface.
```

## Relationship To Other Skills

- can be loaded directly by `repo-reading-system` when the change is already specific
- can be preceded by `repo-onboarding` if the repo is still unfamiliar
- can be followed by `architecture-trace` when deeper runtime reasoning is needed

## File Structure

```text
change-entry-finder/
├── README.md
├── README-ZH.md
├── README-EN.md
├── SKILL.md
└── references/
    └── change-artifacts.md
```
