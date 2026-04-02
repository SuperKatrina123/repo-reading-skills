# Repo Reading Skills

一套用于系统性读懂陌生代码仓库的 AI 编码助手 Skill 集合。

不同于一句「帮我总结这个仓库」，这套系统会将请求路由到最合适的 sub-skill，输出可复用的结构化产物。

## 技能结构

[`repo-reading-system`](./repo-reading-system/) 是主入口 skill，负责理解意图并路由到对应 sub-skill。Sub-skills 都在其目录下：

| Sub-skill | 触发场景 | 关键词 |
|---|---|---|
| [`repo-onboarding`](./repo-reading-system/repo-onboarding/) | 第一次接触陌生仓库、新人交接 | 这个项目是做什么的、从哪里开始读、帮我快速上手、生成 repo brief |
| [`architecture-trace`](./repo-reading-system/architecture-trace/) | 已有基本了解，需要运行时视角 | 请求/事件怎么流转、模块怎么协作、数据怎么流动、系统边界在哪 |
| [`change-entry-finder`](./repo-reading-system/change-entry-finder/) | 改动目标已知，需要找入口和影响面 | 我要改 X 功能从哪里改、改动影响哪些模块、测试要覆盖哪里、风险点在哪 |
| [`repo-knowledge-extractor`](./repo-reading-system/repo-knowledge-extractor/) | 需要沉淀可复用的团队文档 | 提取业务规则、整理技术约定、记录隐性知识、生成避坑指南 |

## 快速开始

大多数情况下直接触发主 skill，让它自动路由：

```text
Use repo-reading-system to help me take over this repository quickly.
```

```text
Use repo-reading-system to explain the runtime architecture of this project.
```

```text
Use repo-reading-system to find where I should modify code to add one API field.
```

```text
Use repo-reading-system to turn this legacy project into a reusable team brief.
```

## 默认输出目录

所有 skill 默认输出到 `docs/repo-brief/`，典型产物：

```
docs/repo-brief/
├── repo-overview.md
├── reading-path.md
├── glossary.md
├── architecture-map.md
├── module-dependency-map.md
├── runtime-flow.md
├── repo-knowledge-base.md
├── pitfalls.md
├── engineering-conventions.md
└── changes/
    └── <topic>/
        ├── change-impact-report.md
        ├── entrypoints.md
        └── test-surface.md
```

## 路由逻辑

```
repo-reading-system
├── 不熟悉这个仓库？           → repo-onboarding
├── 需要了解运行时结构？        → architecture-trace
├── 改动目标已明确？           → change-entry-finder
└── 需要沉淀团队文档？         → repo-knowledge-extractor
```

只加载能回答当前问题的最小 skill 组合，不需要的步骤可跳过。

## 安装使用

这些 skill 是纯 Markdown 文件，适用于任何支持自定义指令的 AI 编码助手。

### GitHub Copilot

将 skill 文件夹复制到项目中，在 `.github/copilot-instructions.md` 中引用：

```md
Use the skills in `.github/skills/repo-reading-system/` for all repo reading tasks.
```

### Claude Code

将 skill 文件夹复制到项目中，在 `CLAUDE.md` 中引用：

```md
## Skills
For repo reading tasks, load the skill from `skills/repo-reading-system/SKILL.md`.
```

### Codex (OpenAI)

将 skill 文件夹复制到项目中，在 `AGENTS.md` 中引用：

```md
## Skills
For repo reading tasks, follow the instructions in `skills/repo-reading-system/SKILL.md`.
```

### 通用方式

任何支持 system prompt 或自定义指令的工具，直接将 `SKILL.md` 的内容粘贴进去即可。

