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

---

## 📝 开发者与社区

### 版本演进 (Changelog)

#### v1.4.0 (2026-03-11)

- **[新增] memory-lancedb-pro 插件完整参考文档**
  - 新增 `references/memory-lancedb-pro.md`，首次完整收录该插件的配置与用法
  - 覆盖：GitHub 地址、安装方式、与内置插件的能力对比、完整 `openclaw.json` 配置示例、所有配置字段说明、可用工具列表
  - 新增每日自动更新 cron 任务说明（触发时机、升级流程、铁律同步逻辑、手动触发命令）
  - 新增诊断命令及常见故障模式（Cloudflare 403 特征识别、gateway/plugin 分层排查）
  - SKILL.md references 表新增对应条目

#### v1.3.0 (2026-03-11)

- **[优化] README 内容扩充**
  - 补充「具体功能」「重要亮点」「当前范围」章节，明确 skill 覆盖边界
  - 强调来自真实环境踩坑、结论可直接执行、本地与远端场景区分等核心定位

- **[同步] 当前本地 openclaw skill 全量同步**
  - 替换仓库内容为最新本地 `~/.codex/skills/openclaw`
  - 移除不再使用的旧版 provider 专属参考与脚本

#### v1.2.0 (2026-03-01)

- **[合并] 合入 win4r/OpenClaw-Skill 通用文档**
  - 将上游社区通用参考内容合并入本仓库
  - 保留本地定制配置，解决与上游文档的冲突

#### v1.1.0 (2026-02-26)

- **[修复] relay 模型白名单格式说明**
  - 明确 model whitelist map 格式，避免配置后 `/model` 命令显示异常

- **[更新] official.md 同步至 OpenClaw v2026.2.23**
  - 更新 v2026.2.23 版本 highlights

#### v1.0.0 (2026-02-22 ~ 2026-02-21)

- **[初始化] 仓库创建与基础内容建立**
  - 创建双语 README（中文优先）
  - 添加 403 账号重验流程协议（`references/relay-tools.md`）
  - 同步 official.md 至 OpenClaw v2026.2.21 / v2026.2.22
  - 建立持续更新策略说明
