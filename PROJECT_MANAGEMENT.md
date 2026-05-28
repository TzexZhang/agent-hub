# Agent Hub 项目管理说明

## 目标

`agent-hub` 是当前工作区自有的 AI Agent 项目映射管理中心。

正式仓库地址：

```text
https://github.com/TzexZhang/agent-hub
```

当前本地子项目范围只包含：

```text
github-sentinel
```

`agent-hub` 负责管理元数据；`github-sentinel` 负责后续具体实现。两者职责分离，
避免把子项目源码、依赖和运行产物混入管理项目。

## 契约：映射配置结构

`projects.yaml` 是正式项目映射配置，建议遵循以下结构：

```yaml
version: 1
self:
  id: agent-hub
  repository:
    name: TzexZhang/agent-hub
    url: https://github.com/TzexZhang/agent-hub

projects:
  - id: github-sentinel
    type: tool-agent
    path: ../github-sentinel
```

必须满足的规则：

- `self.id` 固定表示当前管理项目。
- `self.repository.url` 记录当前管理项目的正式 GitHub 地址。
- `projects[*].id` 必须唯一且稳定，后续脚本、报告和自动化任务都应引用它。
- `projects[*].path` 必须指向本地子项目目录。
- `projects[*].capabilities[*]` 必须存在于 `capability_catalog` 中。
- `repositories[*].project_id` 必须匹配一个已有的 `projects[*].id`。
- 配置文件中只允许记录环境变量名称，不允许写入密钥真实值。

## 父项目与子项目关系

推荐目录关系：

```text
program/
  agent-hub/
    README.md
    PROJECT_MANAGEMENT.md
    projects.yaml
  github-sentinel/
```

`agent-hub` 只保存管理元数据，例如项目标识、路径、能力、负责人、运行方式、
仓库跟踪规则和报告规则。

`github-sentinel` 后续保存 GitHub 跟踪代码、模型 Prompt、测试、部署文件和报告
输出等实现相关内容。

## 能力目录

`capability_catalog` 用来描述当前准备支持的 `github-sentinel` 能力：

- `github.repository_tracking`：跟踪指定 GitHub 仓库。
- `github.update_retrieval`：检索提交、Issue、Pull Request、Release 等仓库更新。
- `github.notification`：发送项目进展通知。
- `github.report_generation`：基于检索到的更新生成项目进展报告。
- `llm.multi_model_reporting`：使用模型生成自然语言报告。
- `runtime.scheduled_tasks`：支持定时任务或后台常驻任务。
- `ui.gradio`：提供图形界面。
- `deploy.docker`：支持容器化部署。

当前不登记其他 Agent 项目能力。

## 如何登记子项目

当前只允许登记 `github-sentinel`。如果未来要增加其他子项目，需要先明确扩展范围，
再补充新的子项目映射。

登记流程：

1. 创建子项目目录。
2. 在 `projects` 中添加 `id`、`path`、`type`、`owner` 和 `status`。
3. 从 `capability_catalog` 中选择该子项目具备或计划具备的能力。
4. 只有在入口命令明确时，才填写 `runtime`。
5. 如果子项目需要跟踪 GitHub 仓库，在 `repositories` 中添加仓库规则。
6. 如果子项目需要生成报告，配置报告周期、语言和输出路径。
7. 私密值必须放在环境变量或密钥管理系统中。

## GitHub Sentinel 配置方式

`github-sentinel` 应作为工具型 Agent 子项目进行映射：

```yaml
projects:
  - id: github-sentinel
    type: tool-agent
    path: ../github-sentinel
    capabilities:
      - github.repository_tracking
      - github.update_retrieval
      - github.notification
      - github.report_generation
      - llm.multi_model_reporting
      - runtime.scheduled_tasks
      - ui.gradio
      - deploy.docker
```

使用 `repositories` 定义需要跟踪的 GitHub 仓库。当前默认跟踪自有仓库
`TzexZhang/agent-hub`。

## 配置归属

放在 `agent-hub`：

- 当前管理项目的 GitHub 地址；
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
- Docker 或部署文件；
- 运行时生成产物。

## 操作规则

1. `agent-hub` 只记录项目关系，不复制子项目源码。
2. `github-sentinel` 可以独立开发、测试和部署。
3. 跨项目报告和看板应读取 `projects.yaml`。
4. 能力名称一旦被脚本或报告引用，应保持稳定。
5. 新增能力必须先登记到 `capability_catalog`，再分配给项目。
6. 不在当前范围内的项目不得写入正式配置。

## 校验清单

- `self.repository.url` 是 `https://github.com/TzexZhang/agent-hub`。
- `projects` 当前只包含 `github-sentinel`。
- `projects[*].path` 指向的子项目目录存在。
- 每个已分配能力都存在于 `capability_catalog`。
- 每个被跟踪仓库都映射到已有项目。
- 只有在入口命令明确时才填写运行命令。
- 报告周期和报告语言是明确值。
- 密钥只以环境变量名称形式出现。
