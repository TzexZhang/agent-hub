# Git Sentinel

`github-sentinel` 是 `agent-hub` 管理的工具型 Agent 子项目，用于订阅 GitHub/Gitee 仓库、抓取仓库动态、生成摘要报告，并向用户隔离的订阅、报告和通知流程提供基础能力。

本目录用于在 `agent-hub` 中记录 `github-sentinel` 的发布版本和版本能力。实现代码仍由同级子项目目录 `../github-sentinel` 维护。

## 项目信息

| 项目         | 内容                |
| ---------- | ----------------- |
| 项目 ID      | `github-sentinel` |
| 项目类型       | 工具型 Agent         |
| 当前版本       | `v2.0.0`          |
| 发布日期       | `2026-07-22`      |
| Python 包版本 | `2.0.0`           |
| 开源协议       | MIT               |
| 运行环境       | Python 3.12+      |

## 版本历史

| 版本号      | 版本特性                                                                                                                                                    | 发布链接                                                                                     |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `v0.0.1` | 支持通过仓库地址订阅 GitHub/Gitee 仓库；公开仓库可不填写访问令牌，私有仓库可配置访问令牌；访问令牌加密保存且不在接口中返回；支持手动抓取仓库动态并生成报告；Push 中的多条 commit 会拆分为独立动态并写入报告；支持按时间范围查看报告；提供轻量 Dashboard 管理订阅和报告。 | [查看 v0.0.1](https://github.com/TzexZhang/github-sentinel/tree/v0.0.1?tab=readme-ov-file) |
| `v0.0.2` | 支持按订阅间隔抓取仓库事件并基于订阅时间窗口生成报告；支持手动选择开始日期和结束日期，先更新事件表再生成 Markdown 报告；支持汇总 Push 和 Issue 相关事件，Push 会按 commit 拆分；支持按外部事件 ID 去重；支持接入内置 LLM 生成项目进展简报，可在智谱免费系列和 Gemini 免费系列间切换；LLM 报告按新增功能、主要改进、修复问题分类；报告名称可按仓库和日期范围生成；Dashboard 支持按订阅仓库查看报告列表、生成时间和 Markdown 正文；报告时间统一展示为 `YYYY-MM-DD HH:mm:ss`；新增环境变量示例文件。 | [查看 v0.0.2](https://github.com/TzexZhang/github-sentinel/tree/v0.0.2?tab=readme-ov-file) |
| `v0.0.3` | 新增 Gradio 可视化界面入口，支持在页面中创建订阅、查看订阅列表、通过操作列删除订阅，并在报告中心完成报告生成与 Markdown 正文预览；报告中心支持按订阅仓库、最近时间范围或自定义日期范围主动查询报告列表；报告列表查询日期和生成报告日期拆分为两组独立条件，默认填入最近一周；日期选择器完成中文化与弹层位置优化；报告预览区域调整为模块内部滚动；报告数据增加日期周期记录，同一订阅仓库、同一日期范围重复生成时更新既有报告；仓库事件汇总范围扩展到 Pull Request，报告整理能力覆盖 Push、Issue、Pull Request。 | [查看 v0.0.3](https://github.com/TzexZhang/github-sentinel/tree/v0.0.3?tab=readme-ov-file) |
| `v0.0.4` | 支持单用户、多仓库订阅管理，可在 Dashboard 中创建、查看、修改和删除仓库订阅；支持按订阅维度配置抓取间隔，系统会在订阅到期后获取当前周期内的新事件并生成报告；支持订阅与通知通道绑定，通知类型覆盖 SMTP 邮箱、企业微信自建应用消息和通用 Webhook；支持在创建或修改订阅时选择通知类型并填写通知目标；支持报告生成后创建通知任务，由应用内 Notification Worker 统一投递通知并记录发送状态、失败原因和重试信息；支持手动生成报告时选择是否发送通知；支持将报告 Markdown 转换为适合不同通道展示的内容；企业微信通知支持通过自建应用向成员账号推送文本消息，并预留接收消息服务器 URL、Token 和 EncodingAESKey 配置入口。 | [查看 v0.0.4](https://github.com/TzexZhang/github-sentinel/tree/v0.0.4?tab=readme-ov-file) |
| `v1.0.0` | 新增本地账号体系，支持注册、登录、退出登录和修改密码；新增 Cookie/Token 会话机制，默认 7 天内免登录；仓库订阅、报告和通知任务按当前登录用户隔离；新增报告管理模块，支持查看报告列表、批量勾选并物理删除报告；新增用户管理模块；报告列表按生成时间倒序展示；企业微信通知支持完整正文发送，内容过长时自动拆分为多条文本消息；Notification Worker 支持单轮处理数量控制，默认每轮处理 50 条待发送任务；项目名称调整为 `Git Sentinel`；仓库订阅通知类型保留“不通知”“邮箱 SMTP”“企业微信通知”。 | [查看 v1.0.0](https://github.com/TzexZhang/github-sentinel/tree/v1.0.0?tab=readme-ov-file) |
| `v1.0.1` | 修复多用户订阅同一仓库时，仓库事件按全局 `external_id` 去重导致后创建订阅无法入库事件的问题；仓库事件唯一性调整为同一订阅内按 `(subscription_id, external_id)` 去重，确保不同用户的相同仓库订阅可以分别生成包含事件内容的报告；新增 `repository_events` 表结构迁移，服务启动时会将旧的全局事件唯一约束平滑调整为订阅级唯一约束，并保留已有事件数据。 | [查看 v1.0.1](https://github.com/TzexZhang/github-sentinel/tree/223d95e378e640932f10f0aecb7c988324b29bd9?tab=readme-ov-file) |
| `v1.0.2` | 手动生成报告时，只要勾选“生成后发送通知”，就会创建新的通知任务并触发发送流程；即使当前时间范围已有历史报告且没有新事件，手动勾选发送通知也会再次创建通知任务；定时任务的通知仍保持去重逻辑，避免同一报告和同一通知通道被定时重复推送。 | [查看 v1.0.2](https://github.com/TzexZhang/github-sentinel/tree/f59fd195b5060a79d7e2207532c1c814b4e525e7?tab=readme-ov-file) |
| `v2.0.0` | `/dashboard` 默认提供全量重构的 React 单页应用，覆盖登录注册、订阅管理、报告生成与管理、账号设置等原 Gradio 交互；保留 Gradio 版本，两版使用相同公开路由，并通过 HttpOnly `github_sentinel_ui_version` Cookie 手动切换；新增类型化报告接口、共享手动报告服务与 OpenAPI 生成客户端，React 和 Gradio 共用业务语义；新增生产/开发 Nginx 分流配置、前端多阶段镜像、桌面与移动端 Playwright E2E，以及后端/前端/浏览器 CI 矩阵；React Dashboard 使用 History 路由，支持直接访问或刷新 `/dashboard/login`、`/dashboard/subscriptions`、`/dashboard/reports` 等嵌套页面；回退时无需更改路由或重新部署，将界面版本切换为 `gradio` 后重新访问 `/dashboard` 即可。 | [查看 v2.0.0](https://github.com/TzexZhang/github-sentinel/tree/ef7bfe915b9e3817fb5eb4c697bfaba8a0e6b4a6?tab=readme-ov-file) |

## 版本管理规则

- `agent-hub/github-sentinel/README.md` 只记录 release 管理信息，不复制 `github-sentinel` 的实现代码。
- 每次 `github-sentinel` 发布新 release 后，应在“版本历史”表格中新增一行。
- 版本号应与 `github-sentinel/pyproject.toml` 中的 `project.version` 保持一致。
- 版本特性只记录该 release 已实现并验证的能力。
- 发布链接指向对应 Git tag 或 release 页面。
