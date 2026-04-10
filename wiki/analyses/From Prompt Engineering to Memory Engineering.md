---
type: synthesis
date: 2026-04-10
tags: [article-draft, knowledge-management, LLM, workflow, prompt-engineering]
---

# From Prompt Engineering to Memory Engineering

## Thesis

The era of prompt engineering — carefully crafting the perfect question to extract a good answer — is giving way to memory engineering: building persistent knowledge architecture that makes every future prompt better by default. The variable is no longer *how you ask*, it's *what the model already knows when you ask*.

## The Shift

For two years, the AI productivity advice was the same: write better prompts. Be specific. Give examples. Use chain-of-thought. The implicit assumption was that each conversation starts from zero and your job is to bridge that gap in a single message.

But as [[Greg Isenberg Agent Skills|Greg Isenberg put it]]: the models are genuinely good now. Claude and GPT are exceptional. The variable is almost always the context you give them. A 1000-line agent.md file burns ~7000 tokens on every run. A skill file? ~50 tokens until activated. The architecture of your context matters more than the wording of your prompt.

[[Andrej Karpathy]] took this further. Instead of tweaking prompts, he built a system: raw sources go in, an LLM compiles a wiki, and every question draws on the accumulated knowledge. At ~100 articles and ~400K words, he found that simple index-based navigation worked without any RAG infrastructure. The LLM reads the index, finds relevant pages, and synthesizes answers with cross-references already in place.

[[Miles Deutscher AI Second Brain|Miles Deutscher]] called it plainly: we've moved from "prompt engineering" to "memory systems engineering." Build the architecture once, then every subsequent prompt is more accurate.

## The Architecture

The [[LLM Wiki]] pattern has three layers:

1. **Raw sources** — your curated collection. Articles, papers, transcripts, notes. Immutable. The LLM reads from them but never modifies them.
2. **The wiki** — LLM-generated markdown files. Summaries, entity pages, concept pages, cross-references. The LLM owns this entirely. You read it; the LLM writes it.
3. **The schema** — a document (CLAUDE.md, AGENTS.md) that tells the LLM how the wiki is structured and what workflows to follow.

The key insight: the wiki is a *persistent, compounding artifact*. The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read. Unlike RAG, which re-derives knowledge from scratch on every query, the wiki keeps getting richer.

## My Journey

It started with Karpathy's tweet on April 2. Within a week:

- Set up Obsidian vault with raw/wiki split, schema in CLAUDE.md
- Ingested 6 sources: a 15,000-word AI forecasting scenario, technical threads, workflow tutorials
- The LLM created 22 wiki pages: 6 source summaries, 6 entity pages, 10 concept pages
- Cross-references emerged automatically — [[AI 2027]]'s intelligence explosion premise connects to [[Karpathy AI Capability Gap|Karpathy's observation]] that coding improves fastest because of verifiable rewards, which connects to [[Context Window Management|why context architecture matters]] more than prompt craft

The graph view in Obsidian showed clusters forming: one around AI forecasting/capability, another around practical AI workflows. Connections I hadn't explicitly made became visible.

## Before and After

**Before (prompt engineering):**
> "I've been reading about AI development timelines and agent workflows. Based on what you know, what are the most important trends in AI right now and how should I think about using AI tools effectively?"

The model gives a generic, well-written answer. It doesn't know what you've read, what you care about, or what connections you've already made.

**After (memory engineering):**
> "Based on the sources in the wiki, what's the relationship between AI 2027's intelligence explosion thesis and Karpathy's observation about peaky AI capabilities? How does this inform how I should set up my own AI workflow?"

The model reads the index, pulls the relevant pages, and synthesizes an answer that:
- References specific claims from specific sources
- Notes where sources agree (coding automation as the catalyst)
- Connects the theoretical (AI 2027's R&D multiplier) to the practical (your skill/MCP setup)
- Builds on previous ingested knowledge rather than starting from scratch

The answer is dramatically better — not because the prompt is better, but because the *context* is richer.

## Why This Works

The tedious part of maintaining a knowledge base is the bookkeeping. Updating cross-references, keeping summaries current, noting contradictions, maintaining consistency. Humans abandon wikis because maintenance grows faster than value. LLMs don't get bored. They can touch 15 files in one pass. The wiki stays maintained because the cost is near zero.

Your job: curate sources, direct analysis, ask good questions. The LLM's job: everything else.

## The Compounding Effect

Each source you ingest doesn't just add — it multiplies. Source #6 connects to sources #1, #3, and #5 in ways you didn't anticipate. The wiki surface area grows, which means future queries have more to draw on, which means query outputs filed back into the wiki are richer, which means the next round of connections is denser.

As Deutscher observed: imagine what this looks like after 3 months, 6 months, a year. It's network effects applied to personal knowledge.

## Getting Started

1. Download Obsidian. Create a vault.
2. Set up directories: `raw/` for sources, `wiki/` for LLM-generated pages.
3. Write a schema file (CLAUDE.md) defining page formats and workflows.
4. Start small: ingest one article. Watch the LLM create pages and connections.
5. Keep going. The system compounds. Every source makes the next one easier.

The right time to stop engineering prompts and start engineering memory is now.

## Sources Consulted
- [[Karpathy LLM Knowledge Bases]]
- [[Greg Isenberg Agent Skills]]
- [[Miles Deutscher AI Second Brain]]
- [[Karpathy AI Capability Gap]]
- [[AI 2027]]
