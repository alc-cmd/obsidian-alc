---
aliases: [agent workflows, AI agents, sub-agents, agentic workflows]
first_mentioned: 2026-04-10
source_count: 1
tags: [AI, agents, workflow, productivity, skills]
---

# AI Agent Workflows

Patterns for building reliable AI agent systems through incremental skill development and careful context management, rather than elaborate upfront configuration.

## Key Aspects
- **Start small**: begin with one agent, one workflow, one skill. Prove it works before expanding
- **Learn by doing**: run workflows manually with the agent first, then have the agent write its own skill from the successful run
- **Iterate on failure**: when skills break, debug collaboratively with the agent, then update the skill file to prevent that failure mode
- **Earn sub-agents**: multi-agent setups should emerge from proven single-agent workflows, not be designed upfront. Setting up 15 sub-agents on day one guarantees failure
- **Your workflow is the moat**: models know everything public. What they lack is your specific process, taste, and way of working. Skills capture this
- **Don't copy skills**: downloading someone else's skill means downloading their context, which won't fit your setup

## Sources
- [[Greg Isenberg Agent Skills]] — The incremental skill-building methodology, with the example of Ross Mike building 5 sub-agents over months

## Open Questions
- How do you decide when a workflow has "earned" its own sub-agent?
- Is there a ceiling on the number of reliable sub-agents one person can maintain?
- How do agent skills interact with [[MCP]] servers — are they complementary or overlapping?

## Related
- [[Context Window Management]], [[MCP]], [[LLM Wiki]]
