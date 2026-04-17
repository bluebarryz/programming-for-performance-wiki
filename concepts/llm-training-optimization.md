---
tags:
  - concept
  - ece459
  - gpu
  - llm
prerequisites:
  - "[[large-language-models]]"
  - "[[gpu-memory-hierarchy]]"
---

# LLM Training Optimization

Optimizing LLM training involves two distinct goals: making the model produce answers or predictions quickly (inference performance), and training the model efficiently (training performance). The course focuses on the configuration space for training, exploring how different knobs affect time, memory usage, throughput, and accuracy.

Training on a GPU is often memory-limited rather than compute-limited. The number of parameters and temporary buffers count toward the GPU's VRAM limit. The course demonstrates this with a bert-base-uncased model on an old GPU with 7611 MiB of VRAM, where even a batch size of 1 with the larger bert-large-uncased model caused an out-of-memory error. Key optimization techniques include adjusting [[batch-size]], [[gradient-accumulation]], [[gradient-checkpointing]], [[mixed-precision-training]], and [[data-preloading]]. Each technique involves tradeoffs between time, memory, throughput, and model quality.

More than any other topic, LLM training exposes the inherent tradeoffs in optimization: memory for CPU, accuracy for time, under-fitting vs over-fitting. The tools and best practices for navigating these tradeoffs are still rapidly evolving.

## Prerequisites
- [[large-language-models]] — These optimizations target LLM training specifically
- [[gpu-memory-hierarchy]] — Many optimizations trade compute for reduced GPU memory usage

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[large-language-models]]
- [[batch-size]]
- [[gradient-accumulation]]
- [[gradient-checkpointing]]
- [[mixed-precision-training]]
- [[data-preloading]]
