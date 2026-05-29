# GitHub Sentinel

`github-sentinel` 是 `agent-hub` 管理的工具型 Agent 子项目，用于订阅 GitHub/Gitee 仓库、抓取仓库动态、生成摘要报告，并为后续通知推送和自动调度提供基础能力。

本目录用于在 `agent-hub` 中记录 `github-sentinel` 的发布版本和版本能力。实现代码仍由同级子项目目录 `../github-sentinel` 维护。

## 项目信息

| 项目         | 内容                |
| ---------- | ----------------- |
| 项目 ID      | `github-sentinel` |
| 项目类型       | 工具型 Agent         |
| 当前版本       | `v0.0.1`          |
| 发布日期       | `2026-05-29`      |
| Python 包版本 | `0.0.1`           |
| 开源协议       | MIT               |
| 运行环境       | Python 3.12+      |

## 版本历史

| 版本号      | 版本特性                                                                                                                                                    | 发布链接                                                                                     |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `v0.0.1` | 支持通过仓库地址订阅 GitHub/Gitee 仓库；公开仓库可不填写访问令牌，私有仓库可配置访问令牌；访问令牌加密保存且不在接口中返回；支持手动抓取仓库动态并生成报告；Push 中的多条 commit 会拆分为独立动态并写入报告；支持按时间范围查看报告；提供轻量 Dashboard 管理订阅和报告。 | [查看 v0.0.1](https://github.com/TzexZhang/github-sentinel/tree/v0.0.1?tab=readme-ov-file) |

## 版本管理规则

- `agent-hub/github-sentinel/README.md` 只记录 release 管理信息，不复制 `github-sentinel` 的实现代码。
- 每次 `github-sentinel` 发布新 release 后，应在“版本历史”表格中新增一行。
- 版本号应与 `github-sentinel/pyproject.toml` 中的 `project.version` 保持一致。
- 版本特性只记录该 release 已实现并验证的能力。
- 发布链接指向对应 Git tag 或 release 页面。

