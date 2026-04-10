---
aliases: [Model Context Protocol, MCP server, MCP servers]
first_mentioned: 2026-04-10
source_count: 2
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

## Open Questions
- How does MCP server quality scale as the ecosystem matures? Will curation become a bottleneck?
- What's the optimal architecture for combining multiple MCP servers without exceeding context limits?
- How do MCP servers compare to native integrations (e.g., built-in web search vs. Tavily MCP)?

## Related
- [[Context Window Management]], [[AI Agent Workflows]], [[LLM Wiki]]
