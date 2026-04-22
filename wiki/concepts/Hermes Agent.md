---
aliases: [Hermes, hermes-agent, Hermes AI Agent]
first_mentioned: 2026-04-15
source_count: 3
tags: [AI-Agent, open-source, self-improving, Skill, MCP, memory]
---

# Hermes Agent

[[Nous Research]] 开源 AI Agent 框架（MIT 协议），核心特性是自改进学习循环——Agent 在执行任务后自动复盘、生成/优化 Skill、积累记忆。两个月 GitHub 47K+ stars，被定位为"会自动进化的 Agent"。

## Key Aspects

### 四层记忆架构
- **L1 常驻提示**：MEMORY.md / USER.md，每次注入 prompt（硬限 3575 字符）
- **L2 会话归档**：SQLite + FTS5 全文索引，LLM 自动摘要 + 关键词召回
- **L3 技能库**：`~/.hermes/skills/` markdown 文件，上下文成本恒定（只加载匹配子集）
- **L4 用户建模**：Honcho（可选），跨会话积累偏好与领域知识

### 自改进学习循环
触发条件：工具调用 >5 次、执行中出错自修复、用户纠正、发现有效但非显而易见的路径。采用 patch 补丁方式更新 Skill，支持 Periodic Nudge 定期回顾优化。

### Skill 生态
- 79 内置 + 47 可选 + 521 社区 = **647 总 Skills**
- 16 个类别：开发(69)、创意(56)、MLOps(42)、研究(38)等
- 格式遵循 agentskills.io 开放标准，理论上可跨平台复用

### MCP 深度集成
- 支持 Stdio（本地子进程）和 HTTP（远程端点）两种 MCP 服务器
- OAuth 2.1 + 恶意软件扫描（v0.8.0+）
- 可通过 `hermes mcp serve` 将自身暴露为 MCP 服务器

### 多 Agent 编排
- 最多 3 个子 Agent 并行执行，各自独立对话历史和终端环境
- 主 Agent 仅接收最终结果——"零上下文代价"并行
- 6 种沙箱后端：Docker、SSH、Daytona、Modal、Singularity、Local

### 消息网关
支持 15+ 通讯平台（Telegram、Discord、Slack、飞书、iMessage、WeChat 等），设计哲学："Agent 藏在用户已有入口后面"。

## 定位对比

| 维度 | Hermes | Claude Code |
|------|--------|-------------|
| 角色 | 无人值守 24/7 后台 | 实时交互编码 |
| Skill | 自动生成 + 社区 647 | 内置 + 插件 |
| 记忆 | 四层 + FTS5 | CLAUDE.md + 手动 |
| 成本 | ~$10-15/月（VPS + API） | 订阅制 |

## 外部批评：Hermes 缺少验证层

[[Garry Tan]] 在 [[Garry Tan Skillify]] 中直接点名 Hermes：`skill_manage` 自动创建/修补 Skill 的能力是"真正出色的程序性记忆"，但缺少软件工程 2005 年就解决的测试习惯：
- 无确定性代码的单元测试
- 无 resolver eval 验证 Skill 路由是否真的命中
- 无 `check-resolvable` 找出"暗 Skill"（无法被触发的孤儿）
- 无 DRY 审计——周一生成 `deploy-k8s`、周四生成 `kubernetes-deploy` 的冲突无人察觉
- 无日常健康检查——上游 API 变形六周后，Skill 静默返回垃圾数据

Garry 的结论："Hermes 负责创建，GBrain 负责验证，你需要两者。" 这直接回应了本页原有的 *"Skill 冲突解决机制是否成熟？"* 问题——现阶段答案是否定的。

## Sources
- [[Hermes Agent Beginner to Master]] — 从安装到实战的完整新手指南，变现路径分析
- [[Hermes Agent Intermediate to Advanced]] — 架构内部机制、Skill 编写、MCP 深度集成、多 Agent 编排
- [[Garry Tan Skillify]] — 外部批评：Hermes 创建能力强，但缺少测试/路由验证/DRY 审计层

## Open Questions
- 自改进天花板在哪？Agent 无法识别超出自身知识范围的错误
- 记忆污染如何管理？早期误记会持续影响后续行为
- Skill 冲突解决机制是否成熟？触发条件重叠时产生意外行为（Garry 的答案：现阶段不成熟，需要外挂 GBrain 级别的审计）
- 647 Skill 的质量分布如何？社区贡献是否经过审核？
- Hermes 能否把 [[Skillify]] 的 10 步检查内建为 `skill_manage` 的验证钩子？

## Related
- [[Skillify]], [[AI Agent Workflows]], [[MCP]], [[Context Window Management]], [[LLM Wiki]]
