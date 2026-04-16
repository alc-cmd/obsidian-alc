---
aliases: [Model Context Protocol, MCP server, MCP servers]
first_mentioned: 2026-04-10
source_count: 4
tags: [AI, tools, Claude, protocol, integrations]
---

# MCP

Model Context Protocol — the standard for connecting Claude (and other LLMs) to external tools and services. MCP servers expose capabilities (search, databases, APIs, browser control, etc.) that Claude can invoke during conversations.

## Key Aspects
- Enables Claude to interact with external systems: web search, databases, code repos, productivity apps, browser automation, and more
- Over 10,000 MCP servers listed across directories as of April 2026, though most are unmaintained
- Install pattern is standardized: `claude mcp add server-name -- npx -y @package/server`
- Each installed server consumes token context for tool descriptions — 3-5 servers is the recommended sweet spot
- Claude Code's Tool Search feature mitigates context cost by lazy-loading server descriptions
- Servers can be scoped per-project or globally (`--scope user`)

## Sources
- [[Top MCP Servers]] — Curated list of 35 production-quality MCP servers across 9 categories
- [[Greg Isenberg Agent Skills]] — Notes that MCP servers consume context tokens, reinforcing the 3-5 server recommendation
- [[Hermes Agent Intermediate to Advanced]] — Hermes 的 MCP 深度集成：Stdio/HTTP 双模式、OAuth 2.1 安全、权限白名单过滤、MCP Sampling 反向调用、动态工具发现

- [[Miles Deutscher TradingView MCP]] — TradingView MCP connecting Claude Code to live chart data for real-time trading analysis, indicator management, and TA automation

## Open Questions
- How does MCP server quality scale as the ecosystem matures? Will curation become a bottleneck?
- What's the optimal architecture for combining multiple MCP servers without exceeding context limits?
- How do MCP servers compare to native integrations (e.g., built-in web search vs. Tavily MCP)?
- Hermes 的 MCP Sampling（服务器反向请求 LLM 推理）模式是否会成为标准？安全影响如何？

## Related
- [[Context Window Management]], [[AI Agent Workflows]], [[LLM Wiki]], [[Hermes Agent]]
