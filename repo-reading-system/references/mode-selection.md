# Mode Selection

Use this reference to choose the smallest correct repo-reading mode.

## Decision Table

| User Need | Primary Mode | Optional Follow-Up |
| --- | --- | --- |
| 刚接手项目，不知道先看什么 | `repo-onboarding` | `architecture-trace` |
| 想知道系统怎么跑起来 | `architecture-trace` | `repo-knowledge-extractor` |
| 要改某个需求，但不知道从哪下手 | `change-entry-finder` | `architecture-trace` |
| 想把仓库知识沉淀成团队资产 | `repo-knowledge-extractor` | `repo-onboarding` |
| 想同时做新人文档和架构图 | `repo-onboarding` | `architecture-trace`, `repo-knowledge-extractor` |

## Minimal Chains

### Chain A: Newcomer Brief

- `repo-onboarding`

Use when the main question is:

- 这仓库是干嘛的
- 先看哪里
- 怎么跑起来

### Chain B: Brief + Runtime

- `repo-onboarding`
- `architecture-trace`

Use when the main question is:

- 先建立整体认知
- 再补系统运行和模块协作

### Chain C: Change Analysis

- `change-entry-finder`

Use when the main question is:

- 我要改哪个点
- 入口文件在哪里
- 会影响哪些测试

If the repo is still too unfamiliar to do this safely, prepend `repo-onboarding`.

### Chain D: Durable Knowledge Base

- `repo-onboarding`
- `repo-knowledge-extractor`

Use when the main question is:

- 想沉淀新人文档
- 想整理术语、约定、坑点
- 想形成长期维护资料

### Chain E: Full Repo Brief

- `repo-onboarding`
- `architecture-trace`
- `repo-knowledge-extractor`

Use only when the user explicitly wants a more complete repo brief package.

## Escalation Rules

- Do not escalate from onboarding to full architecture mapping unless the user asks for runtime understanding or the repo structure makes the overview misleading.
- Do not run knowledge extraction just because it sounds useful; run it when the user wants durable docs, conventions, or pitfalls.
- Do not start change analysis without one concrete change statement.

## Shared Output Root

Default output root for all modes:

- `docs/repo-brief/`

Suggested structure:

```text
docs/repo-brief/
  repo-overview.md
  reading-path.md
  glossary.md
  architecture-map.md
  module-dependency-map.md
  runtime-flow.md
  repo-knowledge-base.md
  pitfalls.md
  engineering-conventions.md
  changes/
    <topic>/
      change-impact-report.md
      entrypoints.md
      test-surface.md
```
