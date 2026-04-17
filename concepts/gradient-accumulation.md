---
tags:
  - concept
  - ece459
  - llm
  - gpu
prerequisites:
  - "[[batch-size]]"
  - "[[llm-training-optimization]]"
---

# Gradient Accumulation

Gradient accumulation calculates gradients in small increments rather than for the whole batch at once, effectively increasing the batch size without proportionally increasing memory usage. The tradeoff is potentially slowing down training by requiring more compute steps.

In the course experiments with batch size 8, increasing gradient accumulation steps from 1 to 4 improved throughput from 7.75 to 8.15 samples/second with memory climbing from 7069 to 7509 MB. Diminishing returns set in quickly. However, higher gradient accumulation increases the effective batch size, which can hurt model quality: the Yelp training results showed accuracy dropping from 0.621 (1 step) to 0.347 (32 steps) to 0.222 (1024 steps), because excessively large effective batch sizes cause the model to overfit or get stuck at local minima.

## Prerequisites
- [[batch-size]] — Gradient accumulation effectively increases batch size without proportional memory cost
- [[llm-training-optimization]] — This is one of the key training optimization techniques

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[batch-size]]
- [[llm-training-optimization]]
- [[large-language-models]]
- [[gradient-checkpointing]]
