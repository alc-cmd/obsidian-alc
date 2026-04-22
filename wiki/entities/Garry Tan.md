---
aliases: [@garrytan, Garry]
first_mentioned: 2026-04-22
source_count: 1
tags: [entrepreneur, AI, investor, skills, testing]
---

# Garry Tan

Founder-operator building personal AI agent infrastructure (OpenClaw) on top of an open-source knowledge engine (GBrain) he authored. Known in the Claude Code / agent-reliability community for the **skillify** pattern — treating every agent failure as a test-backed structural fix rather than a prompt tweak.

## Role & Work

- Author of [GBrain](https://github.com/garrytan/gbrain) — open-source knowledge engine that sits underneath any agent harness; manages the user's brain repo, runs evals, enforces quality gates via `gbrain doctor`
- Author of [GStack](https://github.com/garrytan/gstack) — Claude Code accelerator
- Builder of [OpenClaw](https://openclaw.ai/) — his personal agent, the reference implementation of skillify
- Advocates the "thin harness / fat skills" architecture: keep the runtime harness minimal, let behavior live in testable, versioned skills

## Key Ideas Contributed

- **Skillify** — 10-step pipeline that turns any agent failure into a durable, tested skill (see [[Skillify]])
- **Latent vs deterministic** — reliability framework distinguishing judgment work (LLM) from precision work (code); most agent bugs are deterministic work done in latent space
- **Check-resolvable** — meta-test walking AGENTS.md → SKILL.md → script to find unreachable ("dark") skills
- **Skill creation needs a verification twin** — direct critique of Hermes Agent: great at autonomous skill creation, missing the testing/routing/DRY audit layer that prevents rot

## Sources
- [[Garry Tan Skillify]] — essay laying out skillify, the 10-step checklist, and the critique of LangChain + Hermes

## Related
- [[Skillify]]
- [[Hermes Agent]] — target of Garry's critique
- [[AI Agent Workflows]]
