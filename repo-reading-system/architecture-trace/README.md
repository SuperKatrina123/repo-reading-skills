# Architecture Trace

This sub-skill is for answering how the system actually runs.

It focuses on runtime facts rather than a directory-level overview: where the system starts, how modules collaborate, how data moves, and where state changes.

## When To Use

Use it for questions like:

- Where does the system start?
- How does a request or event flow through the code?
- Which modules are core abstractions and which are adapters?
- Where does state change?
- Where do database, cache, queue, or external side effects happen?

If basic repo understanding is still missing, run `repo-onboarding` first.  
If the desired change is already known, `change-entry-finder` is usually a better fit.

## Default Outputs

Default output root:

```text
docs/repo-brief/
```

Fixed artifacts:

- `architecture-map.md`
- `module-dependency-map.md`
- `runtime-flow.md`

## What This Skill Does

- find primary and secondary entrypoints
- distinguish static dependency from runtime invocation
- trace one or two critical flows
- mark state transitions and side effects
- describe module boundaries and core abstractions

## Example Prompts

```text
Use architecture-trace to explain the runtime architecture of this project.
```

```text
Use architecture-trace to trace one core request flow.
```

```text
Use architecture-trace to output architecture-map, dependency-map, and runtime-flow.
```

## Relationship To Other Skills

- often follows `repo-onboarding`
- can be loaded automatically by `repo-reading-system` when runtime analysis is needed
- does not locate exact code changes; that is the job of `change-entry-finder`

## File Structure

```text
architecture-trace/
├── README.md
├── README-ZH.md
├── README-EN.md
├── SKILL.md
└── references/
    └── architecture-artifacts.md
```
