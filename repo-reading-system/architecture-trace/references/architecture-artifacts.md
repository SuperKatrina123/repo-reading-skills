# Architecture Artifact Structure

## `architecture-map.md`

```md
# Architecture Map

## System Role

## Boundaries

## Primary Entrypoints

## Main Components

## External Dependencies

## Core Abstractions

## Facts / Inferences / Unknowns
```

## `module-dependency-map.md`

```md
# Module Dependency Map

## Choose A Template

- Frontend app: group by runtime structure
- BFF / API app: group by request execution path
- Worker / event-driven app: group by trigger pipeline
- Library: group by public API boundary
```

### Frontend app template

```md
# Module Dependency Map

This repository is a frontend app. Do not flatten everything into one table.

## 1. Entrypoints

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 2. Container / Provider / Context Layer

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 3. State Layer

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 4. Service Layer

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 5. Infrastructure Layer

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |
```

### BFF / API app template

```md
# Module Dependency Map

This repository is a BFF or API app. Organize modules around request execution.

## 1. Routes / Handlers / Functions

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 2. Request Schemas / DTOs

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 3. Usecases / Services

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 4. Repositories / Clients / Integrations

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 5. Middleware / Auth / Observability

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |
```

### Worker / event-driven app template

```md
# Module Dependency Map

This repository is trigger-driven. Organize modules around event flow.

## 1. Triggers / Consumers / Schedulers

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 2. Payload Schemas / Contracts

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 3. Orchestration / Processing Stages

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 4. Side-Effect Integrations

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 5. Retry / Error Handling / Monitoring

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |
```

### Library template

```md
# Module Dependency Map

This repository is a library or shared package. Organize modules around API boundaries.

## 1. Public API Surface

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 2. Adapters / Implementations

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 3. Internal Utilities

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |

## 4. Tests / Examples / Fixtures

| Module | Responsibility | Depends On | Used By | Notes |
| --- | --- | --- | --- | --- |
```

## `runtime-flow.md`

```md
# Runtime Flow

## Flow 1: Primary Path
1. Trigger
2. Entrypoint
3. Orchestration
4. Domain Logic
5. Persistence / Side Effects
6. Output

## Flow 2: Secondary Path

## State Transitions

## Side Effects and Risk Points
```
