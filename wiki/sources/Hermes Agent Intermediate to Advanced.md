---
title: "Hermes Agent 从中级到高级进阶指南"
source_type: guide
author: "composite (official docs + 36kr + community)"
date: 2026-04-15
url: https://hermes-agent.nousresearch.com/docs/
ingested: 2026-04-15
tags: [AI-Agent, Hermes, advanced, Skill, MCP, multi-agent, memory, architecture]
---

# Hermes Agent：从中级到高级进阶

前置阅读：[[Hermes Agent Beginner to Master]]。本文聚焦架构内部机制、Skill 编写、MCP 深度集成、多 Agent 编排与高级调优。

## 四层记忆架构（深入）

| 层级 | 功能 | 技术实现 | 约束 |
|------|------|----------|------|
| L1 常驻提示 | MEMORY.md / USER.md | 每次注入 prompt | 硬限 3575 字符，强制筛选 |
| L2 会话归档 | SQLite + FTS5 全文索引 | LLM 自动摘要 + 关键词召回 | 无自动过期，需手动清理 |
| L3 技能库 | `~/.hermes/skills/` markdown | 可从 40 扩展至 200+，上下文成本不变 | 触发条件重叠时可能冲突 |
| L4 用户建模 | Honcho（可选） | 跨会话积累偏好与领域知识 | 可选组件 |

关键点：L3 技能库的上下文成本恒定——不管有 40 个还是 200 个 Skill，每次推理只加载匹配的子集。

## 学习循环机制（内部流程）

触发条件（满足任一即启动）：
- 工具调用 > 5 次
- 执行中出错但自我修复
- 用户纠正
- 发现有效但不明显的路径

流程：`任务完成 → 自动评估 → 生成/更新 Skill → FTS5 召回 → 用户建模`

更新策略：采用 **patch 补丁方式**（仅修改问题部分，避免全量覆写）。支持 **Periodic Nudge**：系统定期自动提示 Agent 回顾近期操作并优化 Skill。

## Skill 系统（进阶）

### 生态规模
- 79 内置 + 47 可选 + 521 社区 = **647 总 Skills**
- 16 个类别：开发(69)、创意(56)、MLOps(42)、研究(38)、翻译(24)、生产力(12)等
- 格式遵循 **agentskills.io 开放标准**，理论上可跨平台复用（OpenClaw、Claude Code、Cursor）

### 内置 Skill 精选

**开发类**：
- `systematic-debugging`：4阶段根因调查法
- `test-driven-development`：强制 RED-GREEN-REFACTOR 循环
- `subagent-driven-development`：分派独立任务 + 两阶段审查
- `code-review` / `requesting-code-review`：系统化代码审查
- `plan` / `writing-plans`：实施规划（不执行）

**MLOps 类**：
- 训练：axolotl、TRL、GRPO、SimPO、Unsloth、FSDP、PyTorch Lightning
- 推理：vLLM、llama.cpp、TensorRT-LLM、GGUF 量化
- 评估：LLM Harness (60+ benchmark)、W&B
- 向量库：Chroma、FAISS、Pinecone、Qdrant

**自治 Agent 类**：
- `claude-code`：委派编码任务给 Claude Code
- `hermes-agent-spawning`：生成额外 Hermes 实例作为子进程
- `codex` / `opencode`：委派给 OpenAI Codex / OpenCode

**生产力类**：
- `google-workspace`：Gmail、Calendar、Drive、Sheets、Docs
- `linear`：Linear issue/project 管理（GraphQL）
- `notion`：Notion pages/databases/blocks
- `obsidian`：读写 Obsidian vault

### 自定义 Skill 编写

Skill 文件位于 `~/.hermes/skills/`，每个是一个 markdown 文件，包含：
- 名称、描述、步骤、工具调用信息
- Agent 自动生成后可由用户编辑覆盖
- 建议按类别放入子目录

## MCP 深度集成

### 两种服务器类型

**Stdio**（本地子进程，stdin/stdout 通信）：
```yaml
mcp_servers:
  filesystem:
    command: npx
    args: ["-y", "@anthropic-ai/mcp-filesystem"]
    env:
      ROOT_DIR: /path/to/project
```

**HTTP**（远程端点）：
```yaml
mcp_servers:
  internal_api:
    url: https://mcp.company.com/endpoint
    headers:
      Authorization: "Bearer ${INTERNAL_TOKEN}"
    timeout: 30
```

### 工具命名规则
MCP 工具自动加前缀防冲突：`mcp_<server>_<tool>`
- `filesystem.read_file` → `mcp_filesystem_read_file`
- `github.create_issue` → `mcp_github_create_issue`

### 权限过滤（最小权限原则）

白名单模式：
```yaml
tools:
  include: [create_issue, list_issues, get_pull_request]
```

黑名单模式：
```yaml
tools:
  exclude: [delete_customer, refund_payment]
```

白名单优先级高于黑名单。可单独禁用 utility 工具：
```yaml
tools:
  prompts: false
  resources: false
```

### MCP Sampling（LLM 反向调用）
MCP 服务器可通过 `sampling/createMessage` 请求 Hermes 的 LLM 推理：
```yaml
sampling:
  enabled: true
  model: "openai/gpt-4o"
  max_tokens_cap: 4096
  max_rpm: 10
  max_tool_rounds: 5
```

### 动态工具发现
MCP 服务器通过 `notifications/tools/list_changed` 通知 Hermes 工具变更，自动更新无需重启。手动刷新：`/reload-mcp`

### Hermes 作为 MCP Server
`hermes mcp serve` 将 Hermes 暴露为 MCP 服务器，供 Claude Code、Cursor 等调用：
- 10 个工具：conversations_list、messages_send、events_poll 等
- 事件系统：200ms 轮询数据库，近实时感知

### 安全特性（v0.8.0+）
- MCP OAuth 2.1 + 恶意软件扫描
- Stdio env 过滤：只传显式配置的环境变量
- 每服务器隔离：细粒度工具命名空间管理

## 多 Agent 编排

### delegate_task 机制
- 最多 3 个子 Agent 并行执行
- 每个子 Agent 拥有**独立对话历史和终端环境**
- 主 Agent 仅接收最终结果 → "零上下文代价"并行
- 超过 3 个则主 Agent 汇总质量下降

### hermes-agent-spawning
生成额外 Hermes 实例作为独立子进程，适合长时间异步任务。

### 多模型编排
- 主模型：Nous Portal / Claude / OpenRouter / DeepSeek
- 辅助模型（Auxiliary）：处理图像分析、网页提取、Skill 匹配、记忆处理
- 默认 Gemini Flash 处理边角任务，无需手动配置

## 沙箱隔离（6种后端）

| 后端 | 特点 |
|------|------|
| Docker | 只读根文件系统 + 最小权限 + 命名空间隔离（企业级） |
| SSH | 远程服务器执行 |
| Daytona | 云开发环境 |
| Modal | Serverless GPU |
| Singularity | HPC 集群 |
| Local | 本地直接执行（默认） |

## 消息网关

功能最完整的平台：Telegram、Discord、Slack、飞书

支持语音、图片、文件多格式，单一网关进程统一管理所有会话。v0.9.0 新增 iMessage、WeChat 集成。

设计哲学：Agent 藏在用户已有入口后面，而非要求打开专用界面。

## vs 竞品（v0.9.0 基准）

| 维度 | Hermes | OpenClaw | Claude Code |
|------|--------|----------|-------------|
| Stars | 53.2K | 354K | N/A |
| Skill 来源 | 自动生成 + 社区 647 | ClawHub 手动 5000+ | 内置 + 插件 |
| 记忆 | 四层 + FTS5 + Honcho | 静态配置文件 | CLAUDE.md + 手动 |
| 并行 | 3 子 Agent 独立上下文 | 单线程串行 | Agent 工具（无限制） |
| MCP | OAuth 2.1 + 恶意扫描 | 不支持 | 原生支持 |
| 沙箱 | 6 种后端 | 本地优先 | 受限 Bash |
| 训练数据 | Atropos RL 框架 | 无 | 无 |
| 移动端 | Termux/Android | iOS/Android | 无 |

选 Hermes：AI 研究、MLOps、需要 MCP 集成、子代理流水线。
选 OpenClaw：国内企业集成、非技术用户、iOS/Android 端侧。
选 Claude Code：实时交互编码、团队协作开发。

## 高级调优清单

- [ ] 定期审查 `~/.hermes/skills/` 清除过期/冲突 Skill
- [ ] 监控 `~/.hermes/` 目录大小（无自动过期）
- [ ] MCP 配置按最小权限原则白名单化
- [ ] 辅助模型选便宜的（Gemini Flash / DeepSeek）省 token
- [ ] 并发子 Agent 控制在 3 个以内
- [ ] 核心场景保留人工 review——Agent 无法识别超出自身知识范围的错误
