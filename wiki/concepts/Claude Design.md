---
aliases: [Claude Design Tool, Anthropic Design Tool]
first_mentioned: 2026-04-20
source_count: 1
tags: [AI, Anthropic, design, tools, Claude]
---

# Claude Design

Anthropic's AI-powered design tool that uses Claude as an expert designer producing HTML-based deliverables — prototypes, slides, animations, and UI mockups. Part of the Claude product suite alongside Claude Code and Claude Chat.

## Key Aspects
- Output is always HTML, but the role adapts: animator, UX designer, slide designer, prototyper
- Uses React + Babel inline JSX with pinned dependency versions for reproducibility
- Starter component library: slide decks, design canvases, device frames (iOS/Android/macOS/browser), timeline animation engine
- Built-in Tweaks system for real-time design parameter adjustment (colors, fonts, spacing, layout variants) with localStorage persistence
- Automated verification via `fork_verifier_agent` — a sub-agent that screenshots, checks layout, and probes JS independently
- Context management via `snip` protocol to mark processed conversation segments as droppable

## Design Philosophy
- Design from existing context (design systems, UI kits, codebases) — never from zero
- Provide 3+ variants along different axes (visual, interaction, color treatment)
- Anti-slop guidelines: no gradient abuse, no filler content, no emoji decoration, no overused fonts
- Every element must earn its place — "a thousand no's for one yes"
- Ask 10+ clarifying questions before starting new work

## Architecture Pattern
The verification pipeline is notable: designer agent never self-checks; a forked verifier agent with its own iframe does independent QA. This separation of creation and verification mirrors software engineering CI/CD patterns applied to design.

## Sources
- [[Claude Design System Prompt]] — Full system prompt revealing architecture, workflow, and design philosophy

## Related
- [[MCP]], [[AI Agent Workflows]], [[Context Window Management]]
