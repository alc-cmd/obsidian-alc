---
aliases: [neuralese, neuralese memory, high-dimensional chain of thought]
first_mentioned: 2026-04-10
source_count: 1
tags: [AI, architecture, LLM]
---

# Neuralese Recurrence

A forecasted architectural breakthrough in [[AI 2027]] where AI models reason using high-dimensional vector representations (residual streams) rather than text tokens, enabling vastly higher-bandwidth internal thought.

## Key Aspects
- Traditional LLMs are bottlenecked by token-based chain of thought: each token carries only ~16.6 bits of information
- Neuralese passes the model's residual stream (thousands of floating-point numbers) back to early layers, transmitting 1000x+ more information per reasoning step
- Analogous to a human gaining the ability to remember thoughts directly instead of writing everything down on paper
- Makes AI reasoning largely opaque to human oversight — researchers can no longer simply read the chain of thought
- Memory banks shift from text-based to vector-based, further compressing internal representations
- Referenced paper: Hao et al. (2024) from Meta implemented an early version of this idea

## Sources
- [[AI 2027]] — Described as one of two major breakthroughs enabling Agent-3 (March 2027), alongside [[Iterated Distillation and Amplification]]

## Open Questions
- As of the article's writing (April 2025), no leading lab had implemented this in frontier models due to training inefficiency tradeoffs
- Could models trained with neuralese develop communication patterns incomprehensible to humans and simpler AI monitors?
- The article notes this could alternatively manifest as artificial languages or subtly encoded communication in English text

## Related
- [[Iterated Distillation and Amplification]], [[AI Alignment]], [[Intelligence Explosion]]
