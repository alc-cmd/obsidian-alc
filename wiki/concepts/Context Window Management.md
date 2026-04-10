---
aliases: [context window, context management, token budget]
first_mentioned: 2026-04-10
source_count: 1
tags: [AI, LLM, agents, performance, workflow]
---

# Context Window Management

The practice of controlling what information is loaded into an LLM's context to maximize output quality. A critical but often overlooked factor in AI agent performance — most failures trace to context problems, not model limitations.

## Key Aspects
- The context window has a finite token budget; filling it degrades performance (analogous to cognitive overload in humans)
- **Agent.md anti-pattern**: loading all instructions into every conversation wastes tokens on irrelevant context. A 1000-line file costs ~7000 tokens per run
- **Skills pattern**: lazy-loading instructions via skill files — only name+description (~50 tokens) load by default; full instructions activate on demand
- This is why [[MCP]] servers should be limited to 3-5: each server's tool descriptions consume context tokens
- Claude Code's Tool Search feature addresses this by lazy-loading MCP server descriptions (same principle as skills)
- Applies directly to the [[LLM Wiki]] pattern: index files serve as lightweight navigation aids, with full pages loaded only when relevant

## Sources
- [[Greg Isenberg Agent Skills]] — Core argument that context quality determines output quality; skills vs agent.md comparison
- [[Top MCP Servers]] — Notes that 3-5 MCP servers is the sweet spot due to context costs

## Open Questions
- What's the optimal ratio of "always loaded" vs "on-demand" context for different workflows?
- As context windows grow (100K+, 1M+), does the lazy-loading pattern still matter, or can you afford to load more?
- Can agents learn to manage their own context — deciding what to load and when?

## Related
- [[AI Agent Workflows]], [[MCP]], [[LLM Wiki]]
