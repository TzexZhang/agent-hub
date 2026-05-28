# Agent Hub

English | [中文](#中文)

Agent Hub is this workspace's self-owned AI Agent project management hub.

Repository: [TzexZhang/agent-hub](https://github.com/TzexZhang/agent-hub)

The current scope is intentionally small:

- `agent-hub`: parent management project.
- `github-sentinel`: the only planned child project.

`agent-hub` records project mapping, ownership, capability assignment, runtime
intent, repository tracking rules, and report configuration. Child projects keep
their own implementation files.

## English

### Purpose

Use `agent-hub` as the source of truth for the current workspace's agent project
mapping. It answers these questions:

- Which child projects exist?
- Where are they located locally?
- Which capabilities are assigned to them?
- Which GitHub repositories should they track?
- Which runtime and report settings belong to them?

### Current Project Map

```text
program/
  agent-hub/
    README.md
    PROJECT_MANAGEMENT.md
    projects.yaml
  github-sentinel/
```

### Current Scope

Only `github-sentinel` is registered as a child project. Other agent projects
are outside the current scope and should not be added until the scope is
explicitly expanded.

### Configuration Ownership

Use `agent-hub` for:

- child-project identity and local path mapping;
- capability catalog and capability assignment;
- owner, lifecycle status, and operational notes;
- GitHub repository tracking rules;
- report cadence, language, and output target;
- environment variable names required by child projects.

Use `github-sentinel` for:

- implementation code;
- dependency and package manager files;
- tests;
- service entrypoints;
- prompts;
- deployment files;
- generated runtime outputs.

### Files

- `README.md`: project overview.
- `PROJECT_MANAGEMENT.md`: Chinese project management guide.
- `projects.yaml`: formal project mapping configuration.

## 中文

`agent-hub` 是当前工作区自有的 AI Agent 项目管理中心。

仓库地址：[TzexZhang/agent-hub](https://github.com/TzexZhang/agent-hub)

当前范围保持最小：

- `agent-hub`：父级管理项目。
- `github-sentinel`：当前唯一计划增加的子项目。

`agent-hub` 负责记录项目映射、负责人、能力分配、运行意图、GitHub 仓库跟踪
规则和报告配置。子项目负责保存自己的实现文件。

### 项目用途

使用 `agent-hub` 作为当前工作区 Agent 项目映射的事实来源。它回答这些问题：

- 当前有哪些子项目？
- 子项目在本地哪个目录？
- 子项目分配了哪些能力？
- 子项目需要跟踪哪些 GitHub 仓库？
- 子项目使用什么运行方式和报告规则？

### 当前项目结构

```text
program/
  agent-hub/
    README.md
    PROJECT_MANAGEMENT.md
    projects.yaml
  github-sentinel/
```

### 当前范围

当前只登记 `github-sentinel` 一个子项目。其他 Agent 项目不在当前范围内，除非
后续明确扩展范围，否则不应添加。

### 配置归属

放在 `agent-hub`：

- 子项目身份和本地路径映射；
- 能力目录和能力分配；
- 负责人、生命周期状态和管理备注；
- GitHub 仓库跟踪规则；
- 报告周期、语言和输出目标；
- 子项目需要的环境变量名称。

放在 `github-sentinel`：

- 实现代码；
- 依赖和包管理文件；
- 测试；
- 服务入口；
- Prompt；
- 部署文件；
- 运行时生成产物。
