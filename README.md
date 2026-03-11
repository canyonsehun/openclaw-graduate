# openclaw-graduate

> 🌐 语言切换：**中文（当前）** | [English](./README.en.md)

这个仓库保存当前在本地使用的 `openclaw` skill，聚焦 OpenClaw 的安装、升级、模型 provider 配置、channels、multi-agent、relay / codex / Claude 切换、远端 Codespaces 部署与常见故障排查。

## 仓库内容

- `SKILL.md`：主技能说明
- `references/`：分主题操作参考
- `scripts/`：配套脚本
- `assets/`：技能附带素材

## 具体功能

- **安装与修复**：覆盖 `openclaw setup`、`openclaw doctor --repair`、`gateway start/restart/status`、`channels status`、`agents list` 等基础运维流程
- **模型与厂商切换**：整理 `codex`、`anthropic / Claude`、OpenAI-compatible relay 等 provider 的接法、默认模型配置、fallback 规则与 smoke test 方法
- **Bot 与频道接入**：支持 Telegram Bot 接入、agent 绑定、默认模型指定、多 bot 路由，以及 `/model` 可选目录的维护
- **远端部署**：包含 GitHub Codespaces / github.dev 的启动方式、环境变量注入、`~/.secrets/openclaw.env` 约定、远端 Gateway 启动脚本思路
- **插件与记忆排查**：覆盖 `memory-lancedb-pro` 注册、Jina embedding 探针、插件加载异常、session 锁等常见问题
- **Claude Code 联动**：记录远端 Claude Code 可用时如何作为 OpenClaw 的后备执行入口，以及最小冒烟验证方法
- **诊断与回归验证**：给出 403 / 429、Cloudflare challenge、错模型、不回复、配置写死、JSON 配错、路由异常等问题的排查路径

## 重要亮点

- **来自真实环境**：不是纯文档摘抄，而是把本地 macOS、远端 Codespaces、真实 provider 与 bot 配置踩坑后的可用方案沉淀下来
- **结论可直接执行**：尽量给出可落地命令、配置路径、验证方式，不写空泛说明
- **本地与远端分开讲**：明确区分本地可用、远端受限、Cloudflare 拦截、Claude fallback 等不同场景，减少误判
- **聚焦运维与排障**：重点放在“为什么不能用”“现在该改哪里”“怎么验证已经修好”，而不是泛泛介绍 OpenClaw
- **附带辅助脚本**：仓库里保留了一键接入 Telegram Bot、同步 relay 模型目录等脚本，方便直接复用

## 当前范围

- OpenClaw 安装、升级、Gateway 运维
- Telegram / WhatsApp / Slack 等 channel 配置
- 模型 provider 配置与切换
- 远端 Codespaces / github.dev 部署与诊断
- 常见故障排查：403 / 429、错模型、不回复、session 锁、插件注册异常

## 更新原则

- 只同步当前本地 `~/.codex/skills/openclaw` 的有效内容
- 只保留对操作者有价值的流程、命令、配置与排障结论
- 提交前不保留真实 key / token / chat id 等敏感信息
