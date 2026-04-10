---
title: "How Claude Skills + AI Agents Actually Work"
source_type: article
author: Greg Isenberg
date: 2026-04-08
url: https://x.com/gregisenberg/status/2042010418454184325
ingested: 2026-04-10
tags: [AI-agents, Claude, skills, workflow, context-window, productivity]
---

# How Claude Skills + AI Agents Actually Work

Greg Isenberg summarizes a podcast episode with Ross Mike (@Rasmic) that explains why most people fail with AI agents and how to fix it. The core insight: the context window is everything — the quality of what goes in determines the quality of what comes out.

## Key Takeaways
- Agent.md files are mostly wasteful — every line loads into every conversation, burning tokens
- Skills (skill.md) are the real unlock: only ~50 tokens for name+description load by default; full instructions load only when triggered
- Build skills by doing the workflow manually with the agent first, then having the agent write the skill from its own experience
- Iterate recursively: when skills break, debug together, then update the skill file to prevent that failure mode
- Sub-agents are earned, not configured on day one — start with one workflow, prove it works, then expand

## Summary

The thread argues that most AI agent failures come from poor context management, not model limitations. The key distinction is between agent.md files (which load entirely into every conversation, wasting context) and skills (which lazy-load only when needed). The recommended workflow: run a process manually with the agent, let it learn what works, then have it write its own skill file. When that skill breaks, debug it collaboratively and update the file iteratively. Over months, this produces reliable multi-agent setups — Ross Mike built 5 sub-agents covering marketing, business, and personal workflows through this incremental approach.

## Notable Claims
- A 1000-line agent.md file costs ~7000 tokens on every run; a skill costs ~50 tokens until activated
- The agent writes better skills than humans because it has full context of what actually worked in practice
- Models are already excellent — the variable is almost always the context you provide
- Downloading someone else's skills won't work because they weren't built around your specific workflow
- The closer you get to filling the context window, the worse the agent performs

## Connections
- Related to: [[Context Window Management]], [[AI Agent Workflows]]
- Validates: the [[LLM Wiki]] approach of keeping schema lean (CLAUDE.md) and letting the LLM learn patterns incrementally
- Complements: [[MCP]] — skills and MCP servers are both mechanisms for extending Claude's capabilities
