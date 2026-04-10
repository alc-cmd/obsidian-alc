---
title: "Thread by @gregisenberg"
source: "https://x.com/gregisenberg/status/2042010418454184325"
author:
  - "[[@gregisenberg]]"
published: 2026-04-09
created: 2026-04-10
description: "this video is the CLEAREST explanation of how claude skills + AI agents work and how to use them most people set up an AI agent and wonder"
tags:
  - "clippings"
---
**GREG ISENBERG** @gregisenberg [2026-04-08](https://x.com/gregisenberg/status/2042010418454184325)

this video is the CLEAREST explanation of how claude skills + AI agents work and how to use them

most people set up an AI agent and wonder why it keeps disappointing them.

the context window is everything

context is what the model assembles before it takes any action. think of it like everything the agent needs to read before it does anything. the quality of what goes in determines the quality of what comes out. the models are genuinely really good right now. claude and gpt are exceptional. the variable is almost always the context you give them.

1\. agent.md files are mostly unnecessary

every single line you put in an agent.md file gets added to every single conversation you have with your agent. a 1000 line file is around 7000 tokens burning on every run. the model already knows to use react. it can read your codebase. save the agent.md for proprietary information specific to your company that the model genuinely cannot know on its own.

2\. skills are the actual unlock

a skill.md file works differently. what loads into context is only the name and description, around 50 tokens. the full instructions only appear when the agent recognizes it needs that skill. so instead of 7000 tokens on every run you have 50. and the agent stays sharp because the context window stays lean. the closer you get to filling the context window the worse the agent performs, same way you perform worse when someone dumps 10 things on you at once.

3\. here is how to actually build a skill the right way

most people identify a workflow and immediately try to write the skill. what you want to do instead is run the workflow by hand with the agent first. walk it through every single step. tell it what to check, what good looks like, what bad looks like. correct it in real time. once you have had a full successful run from start to finish, tell the agent to review everything it just did and write the skill itself. it writes a better skill than you will because it has the full context of what actually worked in practice not in theory.

4\. recursively building skills is how you go from frustrated to reliable

when the skill breaks, and it will break, ask the agent exactly why it failed. it will tell you specifically what went wrong. fix it together in that same conversation. then tell it to update the skill file so that failure mode never happens again. ross mike did this five times with his youtube report generator. it now pulls from eight different data sources and runs flawlessly every single time without him touching it.

5\. sub agents are something you earn not something you set up on day one

start with one agent. build one workflow. turn it into one skill. once that works add another. ross mike has five sub agents now covering marketing, business, personal and more. it took months to get there and every single one exists because a workflow proved it deserved to exist. the people who set up 15 sub agents on day one and wonder why nothing works skipped all the steps that make the thing actually run.

6\. your workflow is the thing the model cannot get anywhere else

the model has been trained on everything. it knows more than you about most things. what it does not have is your specific process, your taste, your way of doing things. that is what skills capture. that is what makes your agent actually useful versus a generic one. downloading someone else's skill means downloading their context onto your setup and it will not work the way you want it to because it was never built around how you work.

this is the clearest explanation of how agents actually work i have heard. @rasmic runs this stuff every single day and the results show it.

full episode is now live on @startupideaspod where you get your pods

people charge for this sorta stuff

i give away the sauce for free

i just want you to win

watch

---

**Micky** @Rasmic [2026-04-08](https://x.com/Rasmic/status/2042020191236719097)

appreciate u for having me on...

---

**GREG ISENBERG** @gregisenberg [2026-04-09](https://x.com/gregisenberg/status/2042045852848377968)

❣️

---

**Dennis** @tipbtdennis [2026-04-08](https://x.com/tipbtdennis/status/2042013676215910429)

Banger combo

---

**GREG ISENBERG** @gregisenberg [2026-04-08](https://x.com/gregisenberg/status/2042013861172121877)

such a pleasure hanging with the professor @Rasmic

---

**YabsssAI** @yabsssai [2026-04-09](https://x.com/yabsssai/status/2042372049394680172)

that's a huge drop in barrier to entry, going from an unspecified amount of work to just 4 clicks is a game changer for shipping agents.

---

**Jordan Wright** @JordanPriceDesk [2026-04-09](https://x.com/JordanPriceDesk/status/2042077633874424192)

This was such a good breakdown of how to reduce agent md files and get more benefit with skills. So good!

---

**Gagan | Claude + AWS** @gagansaluja08 [2026-04-09](https://x.com/gagansaluja08/status/2042278555690676225)

yeah context is where most agent failures actually live. spent a week debugging an agent last month and the fix was almost always about what was or wasn't in context at the time it made a bad call. the logic was fine, the setup wasn't

---

**André Simões** @oandresimoes [2026-04-09](https://x.com/oandresimoes/status/2042232724686086500)

The skill-writing-itself loop is what most people skip. They want the final skill without iteration. But edge cases only surface in practice. The agent writes better guardrails because it failed first, not in theory.