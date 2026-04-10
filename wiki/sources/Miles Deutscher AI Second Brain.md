---
title: "I Built an AI Second Brain Using Obsidian + Claude (Copy Me)"
source_type: video
author: Miles Deutscher
date: 2026-04-09
url: https://x.com/gregisenberg/status/2042010418454184325
ingested: 2026-04-10
tags: [Obsidian, Claude-Code, second-brain, knowledge-management, LLM, workflow, tutorial]
---

# I Built an AI Second Brain Using Obsidian + Claude (Copy Me)

[[Miles Deutscher]] demonstrates a practical implementation of the [[LLM Wiki]] pattern using Obsidian + Claude Code. The video is a step-by-step tutorial showing how to set up an LLM-maintained personal knowledge base, heavily inspired by [[Andrej Karpathy]]'s viral post. Deutscher adds practical examples from his own content business and suggests strategic upgrades.

## Key Takeaways
- Setup takes ~5 minutes: download Obsidian, create a vault, paste Karpathy's system prompt into Claude Code
- Claude Code edits Obsidian files directly — most interaction happens through Claude Code, not Obsidian's UI
- Obsidian Web Clipper extension enables one-click saving of articles, tweets, and videos into the raw collection
- The system compounds exponentially: network effects mean 6-12 months of use produces dramatically better results
- This represents a shift from "prompt engineering" to "memory systems engineering"
- The knowledge base is portable: works across LLMs, agents, and platforms since it's just markdown files

## Summary

Deutscher walks through building a "second brain" using Obsidian as a visual frontend and Claude Code as the editing backend. He starts with Karpathy's framework (raw sources → LLM-compiled wiki → index + cross-links) and shows practical usage: clipping the "AI 2027" article via Web Clipper, then telling Claude Code to ingest it. Claude Code automatically finds entities (Sam Altman, OpenAI), creates connections, and builds out the wiki graph.

He demonstrates real-world value by querying: "Based on my content strategy and the AI 2027 timeline, what videos should I prioritize?" — Claude returns actionable recommendations drawing on his indexed strategy, video history, and the new article's insights. He notes this is far superior to a single-chat prompt because the agent has access to all accumulated context.

## Notable Claims
- Obsidian's graph view functions like a visual mind map of your knowledge, similar to how the brain forms connections between memories
- The era of "prompt engineering" is giving way to "memory systems engineering" — building architecture once, then every subsequent prompt benefits
- Separate databases for different domains (personal, business, content) prevent things getting messy — Karpathy also recommends this
- Three strategic upgrades suggested:
  1. **Hot cache**: 500-word summary agents read first for instant context
  2. **Self-maintaining wiki**: weekly automated health checks via Claude Code scheduled tasks
  3. **Agent integration**: plug into Discord bots, research agents, autonomous assistants

## Connections
- Directly implements: [[LLM Wiki]] pattern, [[Andrej Karpathy]]'s framework
- Uses: [[MCP]] ecosystem indirectly (Claude Code's tool integration)
- Demonstrates: [[Context Window Management]] — the wiki solves the "constantly re-prompting" problem by making context persistent
- Related to: [[Karpathy LLM Knowledge Bases]] — Deutscher explicitly credits and builds on Karpathy's viral post (16M+ views)
- Author: [[Miles Deutscher]]
