---
title: Garry Tan Skillify
type: source
author: "@garrytan"
published: 2026-04-22
clipped: 2026-04-22
source_url: "https://x.com/garrytan/status/2046876981711769720"
tags: [AI-agents, skills, testing, evals, workflow, GBrain, OpenClaw, Hermes]
---

# Garry Tan Skillify

Essay by Garry Tan arguing that agent reliability is a testing problem, not a prompting problem. Introduces **skillify**: a 10-step checklist that turns every agent failure into a permanent, tested skill, making the bug structurally impossible to repeat. Directly critiques LangChain/LangSmith for shipping testing primitives without an opinionated workflow.

## The Thesis

Most AI agent reliability is "vibes-based" — prompt tweaks, bigger system messages, "please don't hallucinate" incantations. These decay the moment a conversation gets complex. Skillify replaces that with software-engineering discipline: every failure gets a test that lives forever. The bug becomes structurally unreachable.

Two recent agent failures motivated the pattern:

1. **Calendar recall failure** — agent hit blocked live APIs repeatedly before finally searching 3,146 local calendar files that had the answer indexed. Bug: deterministic work (grep) done in latent space (LLM reasoning).
2. **"28 minutes" failure** — agent did UTC→PT math in its head and was off by exactly one hour. A `context-now.mjs` script already existed that returned the correct answer in 50ms. Bug: same shape — deterministic math done in latent space.

**The loop that makes the architecture work**: latent space builds the deterministic tool, then the deterministic tool constrains the latent space. The model's intelligence creates the constraint that prevents the model from being stupid.

## The 10-Step Skillify Checklist

1. **SKILL.md** — the contract (name, triggers, rules)
2. **Deterministic code** — `scripts/*.mjs` (no LLM for what code can do)
3. **Unit tests** — vitest against pure functions and fixture data
4. **Integration tests** — live endpoints, real data
5. **LLM evals** — LLM-as-judge on quality + correctness; catches wrong process even when answer happens to be right
6. **Resolver trigger** — entry in `AGENTS.md` routing table
7. **Resolver eval** — verify the trigger actually routes (false-negative and false-positive cases)
8. **Check-resolvable + DRY audit** — walks AGENTS.md → SKILL.md → script/cron to find unreachable skills and overlapping triggers
9. **E2E smoke test** — full pipeline; agent chooses the skill over winging it
10. **Brain filing rules** — where new knowledge-base pages go (people/, companies/, civic/)

> A feature that doesn't pass all ten is not a skill. It's just code that happens to work today.

## Skillify as a Verb

The checklist started as a failure-response protocol, then became the way Garry builds everything. Workflow: prototype in conversation → see it work → say "skillify" → the prototype becomes permanent infrastructure with tests, resolver entry, and documentation.

Example utterances from his actual transcripts:
- "can you remember this as a webhook skill and skillify it"
- "whenever anything in openclaw needs a headless browser ... skillify it"
- "whenever you send me a link you have to curl it yourself ... skillify it"

One word triggers the full 10-step pipeline.

## Latent vs Deterministic

Core distinction from his [thin harness / fat skills](https://x.com/garrytan/status/2042925773300908103) framework:

- **Latent** — work requiring judgment; LLM space; same input ≠ same output
- **Deterministic** — work requiring precision; code space; same input = same output, every time

Both failures were the same bug: **deterministic work executed in latent space**. The agent had the right tool and chose cleverness instead of discipline.

## Why Hermes Agent Isn't Enough

Explicit critique of [[Hermes Agent]]: its `skill_manage` tool lets the agent create, patch, and delete skills autonomously — genuinely great procedural memory. But Hermes does **not** test its skills:

- No unit tests on deterministic code
- No resolver evals to verify routing
- No `check-resolvable` to find dark (unreachable) skills
- No DRY audit for duplicates
- No daily health check

Failure modes Garry has watched accumulate in untested skill systems:
- Monday: agent creates `deploy-k8s`. Thursday: same agent creates `kubernetes-deploy` from another conversation. Both trigger on similar phrases → ambiguous routing.
- Skill works on day 1. Six weeks later upstream API shape changes. Skill silently returns garbage.
- Autonomously-created skill has weak trigger that never matches → orphan eating index tokens.

**"Without tests, any codebase rots" — software engineering solved this in 2005. Agent skills are no different.** Hermes handles creation; GBrain handles verification. You need both.

## GBrain & OpenClaw

- [OpenClaw](https://openclaw.ai/) — Garry's personal agent harness
- [GBrain](https://github.com/garrytan/gbrain) — open-source knowledge engine underneath any harness; runs evals, enforces quality gates, `gbrain doctor --fix` auto-repairs DRY violations
- **GBrain SkillPack** — portable bundle of skills, resolver triggers, scripts, and tests installable into any agent setup by asking the agent to do it
- [GStack](https://github.com/garrytan/gstack) — Claude Code accelerator

The skillify checklist isn't a suggestion; it's what `gbrain doctor` actually checks.

## Notable Numbers

- 179 unit tests across 5 suites, runs in under 2 seconds
- 35 daily LLM evals on `context-now` skill alone
- 50+ resolver eval test cases
- First `check-resolvable` run on 40+ skills found **6 unreachable** — 15% of system capabilities were dark
- Brain filing audit found 10 of 13 brain-writing skills filing to the wrong directory

## Notable Heuristics

- "The most honest eval heuristic: search your conversation history for when you said 'fucking shit' or 'wtf.' Those are the test cases you're missing."
- "Live calendar APIs are ONLY for events in the FUTURE or the LAST 48 HOURS. Everything historical goes through the local knowledge base first."
- "The trip failure won't happen again. The timezone failure won't happen again. And when the next failure shows up ... it'll get skillified too."

## Source
- Raw: `raw/Clippings/How to really stop your agents from making the same mistakes.md`

## Related
- [[Skillify]] — the concept page for the pattern
- [[Hermes Agent]] — the target of Garry's critique (great creation, missing verification)
- [[AI Agent Workflows]] — skillify is the most opinionated workflow in this space
- [[Context Window Management]] — thin harness / fat skills is the foundational framework
- [[MCP]] — skills vs MCP: skills are procedural memory, MCP is tool access
- [[Greg Isenberg Agent Skills]] — skills-first thesis; Garry extends it with the verification layer Isenberg/Mike didn't cover
- [[Hermes Agent Intermediate to Advanced]] — self-evolving skills without tests; Garry's critique targets exactly this gap
