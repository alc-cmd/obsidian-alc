---
aliases: [LLM knowledge base, LLM-maintained wiki, AI wiki]
first_mentioned: 2026-04-10
source_count: 1
tags: [LLM, knowledge-management, Obsidian, workflow, methodology]
---

# LLM Wiki

A pattern for building personal knowledge bases where an LLM writes and maintains all wiki content, while the human curates sources, directs exploration, and asks questions. The wiki is a persistent, compounding artifact — knowledge is compiled once and kept current, not re-derived on every query (unlike RAG).

## Key Aspects
- **Architecture**: Three layers — raw sources (immutable), the wiki (LLM-generated markdown), and the schema (instructions for the LLM)
- **Operations**: Ingest (process new sources), Query (ask questions against the wiki), Lint (health-check for consistency)
- **Key insight**: The tedious bookkeeping that kills human-maintained wikis (updating cross-references, flagging contradictions, maintaining consistency) costs near-zero for LLMs
- **Navigation**: Index file + brief summaries work well at moderate scale (~100 sources, ~hundreds of pages) without embedding-based RAG
- **Compounding**: Query outputs can be filed back into the wiki, so explorations accumulate alongside ingested sources
- **Lineage**: Related in spirit to Vannevar Bush's Memex (1945) — private, actively curated, with connections as valuable as documents

## Sources
- [[Karpathy LLM Knowledge Bases]] — [[Andrej Karpathy]]'s practitioner description of the pattern, validating the approach at scale

## Open Questions
- At what scale does index-based navigation break down and require proper search (embedding-based or hybrid)?
- Can the pattern extend to collaborative/team wikis with multiple LLM agents and human reviewers?
- How to handle contradictions between sources with differing authority levels?

## Related
- [[Andrej Karpathy]]
