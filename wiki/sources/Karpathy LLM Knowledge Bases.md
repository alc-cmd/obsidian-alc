---
title: "LLM Knowledge Bases (Karpathy Twitter Thread)"
source_type: note
author: Andrej Karpathy
date: 2026-04-02
url: https://x.com/karpathy/status/2039805659525644595
ingested: 2026-04-10
tags: [LLM, knowledge-management, Obsidian, workflow]
---

# LLM Knowledge Bases (Karpathy Twitter Thread)

[[Andrej Karpathy]] describes his workflow for using LLMs to build and maintain personal knowledge bases for research topics. This thread is essentially the practitioner's version of the [[LLM Wiki]] pattern that this vault implements.

## Key Takeaways
- Karpathy's token throughput has shifted from manipulating code to manipulating knowledge (stored as markdown and images)
- The workflow: index sources into `raw/`, LLM "compiles" a wiki of `.md` files with summaries, backlinks, concept pages, and cross-links
- At ~100 articles and ~400K words, simple index-based retrieval works well enough without fancy RAG
- Query outputs (markdown pages, Marp slides, matplotlib charts) get filed back into the wiki, so explorations compound
- LLM "health checks" find inconsistencies, impute missing data, suggest new questions
- Schema kept in `AGENTS.md` (equivalent to this vault's `CLAUDE.md`)

## Summary

Karpathy outlines a personal knowledge management system where LLMs do all the writing and maintenance of a markdown wiki. Raw sources are collected, then an LLM incrementally compiles them into structured wiki pages with summaries, categories, concept articles, and cross-links. He uses Obsidian as the viewing frontend and emphasizes that users rarely edit the wiki directly. He mentions vibe-coding small tools (like a naive search engine) for the LLM to use via CLI. He speculates about future directions including fine-tuning LLMs on the accumulated knowledge.

## Notable Claims
- Index files and brief summaries are sufficient for LLM navigation at moderate scale (~100 sources) — no embedding-based RAG needed
- The process is not fully autonomous: sources are added one by one with human-in-the-loop, especially early on. After enough context, the LLM "gets" the pattern
- Keeps things "super simple and flat" — nested directories of `.md` and `.png` files, no special tooling
- [[Lex Fridman]] confirms using a similar setup for podcast research
- Karpathy sees room for "an incredible new product" in this space

## Connections
- Related to: [[LLM Wiki]], [[Andrej Karpathy]]
- Extends: the general pattern of LLM-maintained knowledge bases that this vault follows
- Validates: the architecture choices in this vault (raw/wiki split, index-based navigation, Obsidian as frontend, schema file)
