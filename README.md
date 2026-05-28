# agent-hub

<p align="center">
  <a href="README-EN.md">English</a> | 中文
</p>

`agent-hub` 是当前工作区自有的 AI Agent 项目管理中心。

仓库地址：[TzexZhang/agent-hub](https://github.com/TzexZhang/agent-hub)

当前范围保持最小：

- `agent-hub`：父级管理项目，用于维护项目映射、能力分配和跨项目配置。
- `github-sentinel`：当前唯一计划增加的子项目，用于后续承载 GitHub 仓库跟踪、
  更新检索、通知和报告生成能力。

`agent-hub` 负责记录项目映射、负责人、能力分配、运行意图、GitHub 仓库跟踪
规则和报告配置。子项目负责保存自己的实现文件。

## 项目用途

使用 `agent-hub` 作为当前工作区 Agent 项目映射的事实来源。它回答这些问题：

- 当前有哪些子项目？
- 子项目在本地哪个目录？
- 子项目分配了哪些能力？
- 子项目需要跟踪哪些 GitHub 仓库？
- 子项目使用什么运行方式和报告规则？

## 当前项目结构

```text
program/
  agent-hub/
    README.md
    README-EN.md
    PROJECT_MANAGEMENT.md
    projects.yaml
    LICENSE
  github-sentinel/
```

## 当前范围

当前只登记 `github-sentinel` 一个子项目。其他 Agent 项目不在当前范围内，除非
后续明确扩展范围，否则不应添加。

## 配置归属

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

## 文件说明

- `README.md`：中文项目概览。
- `README-EN.md`：英文项目概览。
- `PROJECT_MANAGEMENT.md`：项目管理说明。
- `projects.yaml`：正式项目映射配置。
- `LICENSE`：MIT License。

## 开源协议

本项目使用 MIT License，详见 `LICENSE`。
