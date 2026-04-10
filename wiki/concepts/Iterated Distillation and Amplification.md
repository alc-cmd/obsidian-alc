---
aliases: [IDA, distillation and amplification, self-improvement]
first_mentioned: 2026-04-10
source_count: 1
tags: [AI, training, alignment]
---

# Iterated Distillation and Amplification

A training paradigm where AI models are iteratively improved through two alternating steps: amplification (spending more resources to get better outputs) and distillation (training a new model to reproduce those outputs efficiently). Originally proposed by Paul Christiano.

## Key Aspects
- **Amplification**: Run many copies of a model in parallel, allow longer thinking time, use intensive evaluation to filter for the best outputs. Produces higher-quality results at much greater compute cost
- **Distillation**: Train a new model (M1) to imitate the amplified system's outputs, producing a smarter base model that achieves similar quality faster and cheaper. Repeat: amplify M1, distill to M2, etc.
- Historical precedent: AlphaGo used this approach (Monte-Carlo Tree Search + self-play for amplification, RL for distillation) to achieve superhuman Go performance
- In [[AI 2027]], this technique enables Agent-3 to achieve superhuman coding by early 2027
- Previously limited to tasks with clear verification (math, coding), but by 2027 in the scenario, models become good enough at evaluating subjective quality to apply IDA broadly

## Sources
- [[AI 2027]] — One of two key breakthroughs (alongside [[Neuralese Recurrence]]) enabling the leap to Agent-3. Reference: Christiano (2018), Ord (2025)

## Open Questions
- How far can IDA scale before hitting fundamental limits?
- Does the distillation step faithfully preserve the amplified system's capabilities, or does it introduce systematic biases?

## Related
- [[Neuralese Recurrence]], [[Intelligence Explosion]], [[AI Alignment]]
