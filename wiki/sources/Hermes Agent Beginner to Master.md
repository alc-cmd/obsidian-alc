---
title: "Hermes Agent新手教程：从入门到精通"
source_type: guide
author: "花叔 (alchaincyf)"
date: 2026-04-07
url: https://github.com/alchaincyf/hermes-agent-orange-book
ingested: 2026-04-15
tags: [AI-Agent, Hermes, Nous-Research, open-source, self-improving, tutorial]
---

# Hermes Agent：从入门到精通

Nous Research 开源 AI Agent 框架实战指南（橙皮书系列，63页，17章）。Hermes Agent 是首个"出厂就带缰绳"的 AI Agent——内建学习循环、三层记忆、Skill 自动创建与进化，两个月 GitHub 47K+ stars。

## What It Is

Hermes Agent 是 Harness Engineering 概念的首次产品化实现。与手动维护 CLAUDE.md 不同，Skill 由 AI 自行编写、自行改进，用户可覆盖。

三大核心机制：
- **自改进学习循环**：任务完成后自动复盘，决定记什么、提炼成什么 Skill、优化什么规则
- **三层记忆系统**：情景记忆（SQLite + FTS5）→ 语义记忆（持久偏好）→ 程序性记忆（`~/.hermes/skills/` markdown）
- **Skill 系统**：会自我进化的能力模块，越用越精准

## 章节结构

| 部分 | 章节 | 主题 |
|------|------|------|
| 概念篇 | §01-02 | 从 Harness 到 Hermes、60秒全景 |
| 核心机制 | §03-06 | 学习循环、三层记忆、Skill 系统、40+ 工具与 MCP |
| 动手搭建 | §07-11 | 安装配置、初次对话、多平台接入、自定义 Skill、MCP 集成 |
| 实战场景 | §12-15 | 知识助手、开发自动化、内容创作、多 Agent 编排 |
| 深度思考 | §16-17 | 横向对比、自改进边界 |

## 安装（三种方式）

**本地安装**（5分钟）：运行官方一键脚本，编辑 `~/.hermes/config.yaml`

**Docker**：映射 `~/.hermes/` 保持数据持久化

**VPS 24/7**（推荐）：Hetzner CX22 ~$4/月 + OpenRouter，月成本 <$10，内存 <500MB

配置示例：
```yaml
model:
  provider: openrouter
  api_key: sk-or-xxxxx
  model: anthropic/claude-sonnet-4
terminal: local
```

注意：自 2026-04 起 Anthropic 封禁第三方工具通过 Claude 订阅访问，需用 API Key 按量付费。建议用 OpenRouter 灵活切模型。

## 定位对比

| Agent | 角色 | 适用场景 |
|-------|------|----------|
| Claude Code | 白天团队 | 实时交互式编码 |
| Hermes | 夜班团队 | 无人值守 24/7 后台任务 |
| OpenClaw | 企业级 | 可审计配置、合规需求 |

Hermes 适合：长期代码审查/日志监控（cron + GitHub MCP）、个人知识助手、客服/社区 Bot、内容创作。不适合：一次性任务、不愿折腾配置、企业合规。

## v0.9.0 更新（2026-04-13）

"the everywhere release"：Termux/Android 移动端、iMessage/WeChat 集成、Fast Mode、后台监控 Web 仪表板、209 PR 合并。设计哲学：Agent 藏在用户已有入口后面。

## 避坑清单

- 无自动过期：`~/.hermes/` 持续增长，需定期清理
- 记忆污染：早期误记持续影响后续，定期审查 skills/
- 并发上限：最多 3 个子 Agent，超过则汇总质量下降
- Skill 冲突：触发条件重叠时产生意外行为
- 自改进天花板：Agent 无法识别超出自身知识范围的错误

## 商业与变现

### Nous Research 融资

累计 2 轮融资，约 $70M，投资方均为加密领域头部机构。融资以代币计价而非传统股权，核心用于算力储备与团队扩张。CEO Jeffrey Quesnelle 出身以太坊 MEV 基础设施项目 Eden Network。

### 代币化现状

官方仍处于"未发行代币"状态，无明确代币分发机制。但生态中已出现：
- 社区围绕空投预期的讨论
- 第三方平台引导用户参与"潜在奖励"任务
- 链上出现非官方"NOUS"同名代币（与项目无直接关联）

### 个人变现路径（推测）

框架本身免费开源（MIT），无官方订阅/付费。潜在变现方向：
- **Skill 市场**：为特定行业编写定制 Skill 出售
- **托管服务**：帮不会部署的用户搭建 VPS + 配置
- **自动化咨询**：用 Hermes + MCP 编排帮企业搭建工作流
- **内容创作**：利用跨会话记忆做持续输出的内容 pipeline
- **社区 Bot 搭建**：Discord/Telegram/WeChat 客服或社区管理

### 成本结构

| 项目 | 月成本 |
|------|--------|
| VPS (Hetzner CX22) | ~$4 |
| LLM API (OpenRouter) | ~$5-10 |
| 域名/其他 | ~$1 |
| **总计** | **~$10-15/月** |

## 资源

- 橙皮书 PDF：[GitHub 下载](https://github.com/alchaincyf/hermes-agent-orange-book)
- 全系列橙皮书：huasheng.ai/orange-books
- 中英双语版本可用
