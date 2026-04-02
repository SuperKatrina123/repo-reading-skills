---
name: architecture-trace
description: Use when a repository is already roughly understood but the user needs the real runtime picture: system boundaries, entrypoints, module collaboration, request or event flow, data movement, state transitions, and core abstractions.
---

# Architecture Trace

Turn a repo scan into a runtime map that explains how the system actually moves.

## Output Contract

Write these files into the target repo by default:

- `docs/repo-brief/architecture-map.md`
- `docs/repo-brief/module-dependency-map.md`
- `docs/repo-brief/runtime-flow.md`

Use [references/architecture-artifacts.md](references/architecture-artifacts.md) for the default structure.

## Core Questions

This skill must answer:

- Where does the system start?
- What are the meaningful boundaries?
- Which modules call which other modules?
- How do request, event, or data flows move?
- Where does state change?
- Which abstractions are central and which are adapters?

## Hard Rules

1. Prefer one or two critical flows over a vague overview.
2. Distinguish static dependency from runtime invocation.
3. Separate evidence-backed flow from inferred flow.
4. Mark side effects explicitly: database, cache, queue, network, file IO.
5. Show stable abstractions and unstable integration edges separately.
6. Do not force every repository into one flat module table. Choose the module-map shape based on repository type.

## Workflow

### Phase 0: Choose the Slice

Decide:

- repo root or subsystem path
- which runtime path matters most
- whether the system is request-driven, event-driven, job-driven, or library-driven
- which module-map template fits the repo shape

Choose the module-map template before writing `module-dependency-map.md`:

- **Frontend app**
  - group by runtime structure
  - typical sections: entrypoints, container/provider/context, state, services, infrastructure
  - add business-module groups only when they materially help
- **BFF / API app**
  - group by request execution path
  - typical sections: routes/handlers/functions, request schemas/DTOs, usecases/services, repositories/clients, middleware/observability
- **Worker / event-driven app**
  - group by trigger and pipeline stages
  - typical sections: consumers/triggers, payload schemas, orchestration, side-effect integrations, retry/error handling
- **Library / shared package**
  - group by public API and internal implementation zones
  - typical sections: exported API, adapters, internal utilities, tests/examples

### Phase 1: Find Boundaries and Entrypoints

Inspect:

- app/server boot files
- router/handler registration
- worker or consumer registration
- schedulers and cron entrypoints
- framework lifecycle files

Write down:

- primary entrypoints
- secondary/background entrypoints
- internal modules
- external dependencies and adapters

### Phase 2: Trace One or Two Flows

Follow a concrete path end to end:

- input or trigger
- validation / parsing
- orchestration layer
- domain logic
- persistence / outbound effects
- returned state or emitted events

If multiple flows exist, choose the most business-critical one first.

### Phase 3: Map State and Dependencies

Capture:

- which module owns which state
- mutation points
- sync vs async boundaries
- fan-in / fan-out hotspots
- contracts between modules

Do not default to "all important files in one table".

Instead:

- for frontend apps, prioritize runtime layers over component inventories
- for BFFs, prioritize handler-to-integration chains over folder trees
- for workers, prioritize trigger-to-side-effect pipelines
- for libraries, prioritize public API boundaries

### Phase 4: Write the Artifacts

Produce:

- `architecture-map.md`: boundaries, components, roles, high-level interactions
- `module-dependency-map.md`: modules grouped using the repo-type-appropriate template
- `runtime-flow.md`: one or two narrated execution traces

## Review Checklist

- Are entrypoints concrete files?
- Are diagrams or tables tied to code evidence?
- Are caches, queues, and external services called out?
- Are state transitions explicit?
- Are unknown production-only details listed as unknown?
- Does the module map fit the application type instead of forcing a generic flat table?
