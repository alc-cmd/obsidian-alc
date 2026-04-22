---
aliases: [skillify, skillify pattern, skillify checklist]
first_mentioned: 2026-04-22
source_count: 1
tags: [AI-agents, skills, testing, evals, reliability, workflow]
---

# Skillify

A practice for making agent failures structurally impossible to recur. Every failure becomes a SKILL.md with deterministic code and tests; every skill is routed from a resolver; every routing decision is itself evaluated; duplicates and dark skills are audited daily. Coined by [[Garry Tan]] as both a checklist and a verb ("skillify it").

## The Core Loop

**Latent space builds the deterministic tool → the deterministic tool constrains the latent space.**

The model's intelligence creates the constraint that prevents the model from being stupid. The agent uses judgment (latent) to author `calendar-recall.mjs`; the skill then forces the agent to run that script instead of reasoning about calendar data in its head.

## The Latent / Deterministic Distinction

| Space | When | Property |
|-------|------|----------|
| **Latent** | Work requiring judgment | Same input ≠ same output; LLM reasoning appropriate |
| **Deterministic** | Work requiring precision | Same input = same output; code, not model |

Most agent bugs Garry classifies are **deterministic work executed in latent space** — calendar grep done as API spelunking, UTC→PT math done as mental arithmetic. Skillify forces the work into the right space.

## The 10-Step Checklist

Skillify is not complete until all ten pass:

1. `SKILL.md` — contract (name, triggers, rules)
2. Deterministic code — `scripts/*.mjs`
3. Unit tests (vitest)
4. Integration tests against real data
5. LLM evals — LLM-as-judge, catches wrong *process* even when answer is right
6. Resolver trigger entry in `AGENTS.md`
7. Resolver eval — verify the trigger actually routes
8. Check-resolvable + DRY audit — no dark skills, no overlapping triggers
9. E2E smoke test — agent picks the skill over winging it
10. Brain filing rules — where new pages go in the knowledge base

> A feature that doesn't pass all ten is not a skill. It's just code that happens to work today.

## As a Verb

In Garry's daily workflow: prototype in conversation → see it work → say "skillify it" → the 10-step pipeline runs. One word triggers code, SKILL.md, tests, resolver entry, audits.

This is the workflow piece Garry argues $160M of LangChain funding missed — not the testing primitives, but the opinionated sequence and the single trigger word.

## Why It Matters

- **Reliability by construction** — each failure becomes permanent infrastructure, not a prompt patch
- **Catches silent rot** — `check-resolvable` caught 15% dark skills in Garry's own 40-skill system; LLM evals catch *process* failures (mental math) even when the output is occasionally correct
- **Composable** — GBrain SkillPacks are portable bundles; skills written for one agent can install into another

## Critique of Alternatives

- **LangChain / LangSmith** — has trajectory evals, trace-to-dataset, LLM-as-judge, regression suites, unit test frameworks. No opinionated workflow. "Pieces aren't a practice."
- **[[Hermes Agent]]** — genuinely great at autonomous skill *creation* (`skill_manage` tool patches skills after tasks succeed or fail). But no unit tests, no resolver evals, no DRY audit, no daily health check. "Without tests, any codebase rots" — agent skills are the same.

The claim: you need **creation + verification**. Hermes gives creation; GBrain gives verification; skillify is the workflow that binds them.

## Implementation Anchor

Skillify ships in [GBrain](https://github.com/garrytan/gbrain). `gbrain doctor` checks the 10 steps; `gbrain doctor --fix` auto-repairs DRY violations guarded by git working-tree checks. GBrain SkillPacks make the pattern portable across agent harnesses (OpenClaw, Hermes, etc.).

## Sources
- [[Garry Tan Skillify]] — origin essay, the two motivating failures, the full 10-step checklist

## Open Questions
- Does the 10-step checklist scale past ~100 skills, or do the audits themselves become bottlenecks?
- Which steps are essential vs. nice-to-have for a team that can't run daily evals?
- How should skillify interact with Hermes' autonomous skill creation — does the agent itself run the 10 steps, or only a human?
- What is the failure mode when an LLM-judge eval is itself wrong? Who tests the judge?

## Related
- [[AI Agent Workflows]] — skillify is the most opinionated workflow in this family
- [[Hermes Agent]] — the critique target; creation without verification
- [[Context Window Management]] — thin harness / fat skills is the foundational architecture
- [[MCP]] — skills are procedural memory; MCP is tool access; both are required primitives
