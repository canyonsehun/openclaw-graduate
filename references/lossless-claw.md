# lossless-claw 插件

**GitHub**: https://github.com/Martian-Engineering/lossless-claw
**包名**: `@martian-engineering/lossless-claw`
**当前 GitHub 作者 / 维护者**: `Martian-Engineering`
**最新已验证 release**: `v0.5.2`（2026-03-26）
**OpenClaw 中的定位**: `contextEngine` 插件，不是 `memory` 插件

## 简介

`lossless-claw` 是 OpenClaw 的 **LCM（Lossless Context Management）插件**。它解决的不是“跨会话长期记忆”，而是 **单个超长会话里，旧消息被上下文窗口挤掉后，如何尽量无损保留和再展开**。

核心能力：

- 把历史消息写入本地 `SQLite`
- 对旧消息做分层压缩 / 总结
- 在需要时把早期内容按层展开
- 给 Agent 提供主动检索和展开工具

当前可用工具：

- `lcm_grep`
- `lcm_describe`
- `lcm_expand`
- `lcm_expand_query`

## 和 memory-lancedb-pro 的分工

这两个插件 **不是替代关系**，而是互补关系：

| 插件 | 解决的问题 |
|---|---|
| `memory-lancedb-pro` | 跨会话长期记忆、事实/决策沉淀、主动召回 |
| `lossless-claw` | 单个长会话里的旧上下文压缩、保留、展开 |

如果用户问“为什么长对话前面说过的话后面忘了”，优先看 `lossless-claw`。
如果用户问“为什么上次聊过的经验这次没记住”，优先看 `memory-lancedb-pro`。

## 安装方式

```bash
openclaw plugins install @martian-engineering/lossless-claw
```

安装后，在 `openclaw.json` 中把 `contextEngine` 槽位切到它：

```json
"plugins": {
  "slots": {
    "contextEngine": "lossless-claw"
  },
  "entries": {
    "lossless-claw": {
      "enabled": true,
      "config": {
        "summaryModel": "codex/gpt-5.2"
      }
    }
  }
}
```

## 当前环境里验证过的配置经验

### 1. 不要把它当成记忆插件

`lossless-claw` 是 `contextEngine`，不负责替代 `memory-lancedb-pro`。
如果把它误当成“长期记忆插件”，后续会把跨会话记忆问题和长会话上下文问题混在一起。

### 2. 建议和 memory-lancedb-pro 同时用

当前更稳的组合是：

- `plugins.slots.memory = memory-lancedb-pro`
- `plugins.slots.contextEngine = lossless-claw`

这样：

- `memory-lancedb-pro` 负责长期记忆
- `lossless-claw` 负责长对话上下文

### 3. 压缩总结模型不要用太贵

当前环境里已验证，把 `summaryModel` 单独压到便宜模型更合适，例如：

```json
"summaryModel": "codex/gpt-5.2"
```

这样做的原因：

- 它负责“压缩总结”，不是主执行模型
- 用 `gpt-5.4` 做 compaction 没必要，成本高
- 当前环境已经验证 `codex/gpt-5.2` 可正常作为 compaction 模型

### 4. 验证方式

基础验证：

```bash
openclaw plugins info lossless-claw
openclaw agent --agent main --message "reply only: ok" --json
```

功能验证思路：

1. 在同一个会话先输入几条固定信息
2. 再灌一轮无关长内容
3. 最后要求 Agent 回忆早期细节

如果它在长会话里更稳地找回早期内容，说明 `lossless-claw` 已介入。

## 注意事项

- `lossless-claw` 解决的是“长对话抗遗忘”，不是知识库发布器
- 它和 `memory-lancedb-pro` 一样属于插件层能力，但职责不同
- 如果用户只想解决“这次对话太长前面忘了”，不要把问题误导到长期记忆库配置上
