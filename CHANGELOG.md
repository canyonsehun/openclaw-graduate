# Changelog

## v1.4.0 (2026-03-11)

### 新增
- 新增 `references/memory-lancedb-pro.md`：memory-lancedb-pro 插件完整参考文档
  - GitHub 地址：https://github.com/win4r/memory-lancedb-pro
  - 与内置 memory-lancedb 的能力对比（BM25、Hybrid 检索、Cross-encoder 重排序、时间衰减等）
  - 安装方式（git clone + npm install + load path 注册，非 plugins install）
  - 完整 `openclaw.json` 配置示例（含 Jina embedding、hybrid retrieval、rerank 全参数）
  - 所有配置字段说明及当前默认值
  - 可用工具列表（memory_recall / memory_store / memory_forget / memory_update / self_improvement_log）
  - 每日自动更新 cron 任务说明（触发时机、升级流程、铁律同步逻辑）
  - 诊断命令及常见故障模式

### 解决问题
- 此前 skill 中 memory-lancedb-pro 仅有 3 处零散提及，无法指导配置或排查问题
- 补全后 AI 可从 skill 直接获取插件安装、配置、工具使用和故障排查全流程

### 变更文件
- `SKILL.md` — references 表新增 memory-lancedb-pro 条目
- `references/memory-lancedb-pro.md` — 新增

---

## v1.3.0 (2026-03-11)

### 新增 / 优化
- README 补充「具体功能」「重要亮点」「当前范围」章节
- 明确 skill 覆盖边界，强调来自真实环境、结论可直接执行

### 变更文件
- `README.md` — 内容扩充
- 全量同步本地 `~/.codex/skills/openclaw`，移除旧版 provider 专属脚本

---

## v1.2.0 (2026-03-01)

### 合并
- 合入 win4r/OpenClaw-Skill 上游社区通用文档
- 保留本地定制配置，处理合并冲突

---

## v1.1.0 (2026-02-26)

### 修复
- 明确 relay 模型白名单（model whitelist map）格式，修复 `/model` 命令显示异常问题

### 更新
- `references/official.md` 同步至 OpenClaw v2026.2.23 highlights

---

## v1.0.0 (2026-02-21)

### 初始化
- 创建仓库，建立双语 README（中文优先 + English）
- 建立持续更新策略（只同步本地有效内容，不保留 key/token 等敏感信息）
- 添加 403 账号重验流程协议
- 同步 `references/official.md` 至 OpenClaw v2026.2.21 / v2026.2.22
