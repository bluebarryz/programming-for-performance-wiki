---
tags:
  - concept
  - ece459
  - llm
  - gpu
prerequisites:
  - "[[fp32-vs-fp64]]"
  - "[[llm-training-optimization]]"
---

# Mixed-Precision Training

Mixed-precision training is a straightforward tradeoff of accuracy for speed in LLM training. While the default for most values is 32-bit floating point, if full precision is not needed then some of those 32-bit types can be replaced with 16-bit types (or smaller), speeding up calculations.

This directly applies the [[fp32-vs-fp64]] principle: lower-precision arithmetic runs faster on GPUs because more operations fit in the same hardware resources. The approach is particularly effective because many parts of neural network training (like gradient updates) do not require full 32-bit precision. The key is identifying which computations can tolerate reduced precision without degrading model quality.

## Prerequisites
- [[fp32-vs-fp64]] — Mixed precision applies the FP32/FP64 performance tradeoff to training
- [[llm-training-optimization]] — Mixed precision is one of the key training optimization techniques

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[fp32-vs-fp64]]
- [[llm-training-optimization]]
- [[batch-size]]
- [[gradient-checkpointing]]
