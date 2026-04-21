---
title: Claude Design System Prompt
type: source
author: "@ZaynHao"
published: 2026-04-18
clipped: 2026-04-20
source_url: "https://x.com/ZaynHao/status/2045526580903260593"
tags: [Claude, Anthropic, design, system-prompt, AI-tools]
---

# Claude Design System Prompt

Chinese translation of the full system prompt powering Claude Design — Anthropic's design artifact tool. Reveals the complete architecture: workflow, output patterns, component system, and verification pipeline.

## Key Takeaways

**Design Workflow (6 Steps)**
1. Understand user needs — ask clarifying questions for new/ambiguous tasks
2. Explore provided resources — read design system definitions and linked files
3. Plan and create a todo list
4. Set up folder structure, copy resources
5. Finish: call `done` to present file, then `fork_verifier_agent` for automated QA
6. Extremely brief summary — only notes and next steps

**Core Architecture**
- Output medium is HTML — but the role shifts per task: animator, UX designer, slide designer, prototype designer
- Uses React + Babel for inline JSX prototyping with pinned versions and integrity hashes
- Starter components: `deck_stage.js` (slides), `design_canvas.jsx` (static comparisons), device frames (iOS/Android/macOS/browser), `animations.jsx` (timeline engine)
- Tweaks system: in-page controls for real-time design adjustments (color, font, spacing, layout variants), persisted via `postMessage` + JSON markers in source

**Design Philosophy**
- Never add filler content — every element must earn its place ("a thousand 'no's for one 'yes'")
- Always gather design context (UI kit, design system, codebase) before starting — designing from zero is "last resort"
- Provide 3+ variants along different dimensions (visual, interaction, color)
- Mix "safe, pattern-matching" designs with "novel, surprising" ones
- Use oklch for colors harmonizing with existing palettes
- Avoid AI slop: gradient overuse, emoji decoration, left-border accent containers, SVG illustrations, overused fonts (Inter, Roboto, Arial)

**Verification Pipeline**
- `done` tool opens file in preview, returns console errors
- `fork_verifier_agent` spawns background subagent with its own iframe for screenshot + layout + JS checks
- Designer never self-verifies — relies on verifier agent

**Multi-Option Exploration**
- At least 10 questions to user before starting
- Always ask about desired tweak dimensions, variant count, visual divergence tolerance
- Expose variants as tweaks in single file rather than multiple files

**Content Rules**
- Slides: min 24px text at 1920×1080, letterbox scaling with `transform: scale()`
- Mobile: min 44px touch targets
- Persistent slide position via localStorage
- Never use `scrollIntoView` — can break web apps

## Significance

Reveals Anthropic's approach to AI-assisted design tooling: heavy emphasis on design context gathering, automated QA verification, and structured variant exploration. The anti-slop guidelines and design philosophy sections are particularly instructive for anyone building AI design tools or prompting design workflows.

## Source
- Raw: `raw/Clippings/Claude Design 系统提示词（中文版）.md`

## Related
- [[MCP]] — Claude Design exists alongside MCP-connected tools
- [[AI Agent Workflows]] — Verification agent pattern (fork_verifier_agent) is a sub-agent workflow
- [[Context Window Management]] — Snip protocol for managing context during long design sessions
