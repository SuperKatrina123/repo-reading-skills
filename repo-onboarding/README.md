# Repo Onboarding

This sub-skill is for the first pass on an unfamiliar repository.

Its goal is not to explain every line of code. Its goal is to help a newcomer build a reliable high-level model quickly and get a clear reading order.

## When To Use

Use it for questions like:

- What does this repository do?
- Which files should I read first?
- How do I start and verify the project locally?
- Which directories matter most?
- Which terms should I understand early?

If the real question is how the system runs, use `architecture-trace`.  
If the desired change is already known, use `change-entry-finder`.

## Default Outputs

Default output root:

```text
docs/repo-brief/
```

Fixed artifacts:

- `repo-overview.md`
- `reading-path.md`
- `glossary.md`

## What This Skill Does

- identify repo purpose and scope
- extract stack, startup flow, and test commands
- filter the directories and entry files that matter
- build an explicit reading path
- collect terms that commonly block newcomers

## Example Prompts

```text
Use repo-onboarding to help me take over this repository quickly.
```

```text
Use repo-onboarding to create a newcomer reading path for this project.
```

```text
Use repo-onboarding to output repo-overview, reading-path, and glossary.
```

## Relationship To Other Skills

- this is the starting skill for repo reading
- it is often the first step under `repo-reading-system`
- the most common follow-up is `architecture-trace`

## File Structure

```text
repo-onboarding/
├── README.md
├── README-ZH.md
├── README-EN.md
├── SKILL.md
└── references/
    └── repo-brief-structure.md
```
