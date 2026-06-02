# GitHub Sentinel

`github-sentinel` 是 `agent-hub` 管理的工具型 Agent 子项目，用于订阅 GitHub/Gitee 仓库、抓取仓库动态、生成摘要报告，并为后续通知推送和自动调度提供基础能力。

本目录用于在 `agent-hub` 中记录 `github-sentinel` 的发布版本和版本能力。实现代码仍由同级子项目目录 `../github-sentinel` 维护。

## 项目信息

| 项目         | 内容                |
| ---------- | ----------------- |
| 项目 ID      | `github-sentinel` |
| 项目类型       | 工具型 Agent         |
| 当前版本       | `v0.0.3`          |
| 发布日期       | `2026-06-01`      |
| Python 包版本 | `0.0.3`           |
| 开源协议       | MIT               |
| 运行环境       | Python 3.12+      |

## 版本历史

| 版本号      | 版本特性                                                                                                                                                    | 发布链接                                                                                     |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `v0.0.1` | 支持通过仓库地址订阅 GitHub/Gitee 仓库；公开仓库可不填写访问令牌，私有仓库可配置访问令牌；访问令牌加密保存且不在接口中返回；支持手动抓取仓库动态并生成报告；Push 中的多条 commit 会拆分为独立动态并写入报告；支持按时间范围查看报告；提供轻量 Dashboard 管理订阅和报告。 | [查看 v0.0.1](https://github.com/TzexZhang/github-sentinel/tree/v0.0.1?tab=readme-ov-file) |
| `v0.0.2` | 支持按订阅间隔抓取仓库事件并基于订阅时间窗口生成报告；支持手动选择开始日期和结束日期，先更新事件表再生成 Markdown 报告；支持汇总 Push 和 Issue 相关事件，Push 会按 commit 拆分；支持按外部事件 ID 去重；支持接入内置 LLM 生成项目进展简报，可在智谱免费系列和 Gemini 免费系列间切换；LLM 报告按新增功能、主要改进、修复问题分类；报告名称可按仓库和日期范围生成；Dashboard 支持按订阅仓库查看报告列表、生成时间和 Markdown 正文；报告时间统一展示为 `YYYY-MM-DD HH:mm:ss`；新增环境变量示例文件。 | [查看 v0.0.2](https://github.com/TzexZhang/github-sentinel/tree/v0.0.2?tab=readme-ov-file) |
| `v0.0.3` | 新增 Gradio 可视化界面入口，支持在页面中创建订阅、查看订阅列表、通过操作列删除订阅，并在报告中心完成报告生成与 Markdown 正文预览；报告中心支持按订阅仓库、最近时间范围或自定义日期范围主动查询报告列表；报告列表查询日期和生成报告日期拆分为两组独立条件，默认填入最近一周；日期选择器完成中文化与弹层位置优化；报告预览区域调整为模块内部滚动；报告数据增加日期周期记录，同一订阅仓库、同一日期范围重复生成时更新既有报告；仓库事件汇总范围扩展到 Pull Request，报告整理能力覆盖 Push、Issue、Pull Request。 | [查看 v0.0.3](https://github.com/TzexZhang/github-sentinel/tree/v0.0.3?tab=readme-ov-file) |

## 版本管理规则

- `agent-hub/github-sentinel/README.md` 只记录 release 管理信息，不复制 `github-sentinel` 的实现代码。
- 每次 `github-sentinel` 发布新 release 后，应在“版本历史”表格中新增一行。
- 版本号应与 `github-sentinel/pyproject.toml` 中的 `project.version` 保持一致。
- 版本特性只记录该 release 已实现并验证的能力。
- 发布链接指向对应 Git tag 或 release 页面。
