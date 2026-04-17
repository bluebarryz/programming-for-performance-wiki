---
tags:
  - concept
  - ece459
  - llm
  - gpu
prerequisites:
  - "[[llm-training-optimization]]"
  - "[[gpu-memory-hierarchy]]"
---

# Data Preloading

Data preloading addresses the bottleneck of getting data to the GPU faster during LLM training. It involves two techniques: using pinned memory and using multiple threads for data transfer.

Pinned memory (from operating systems concepts) consists of pages that the OS is instructed not to swap to disk, keeping them resident in RAM for faster access. Multi-threading allows overlapping data transfer with computation. Both techniques aim to reduce the time the GPU spends waiting for data, which can be the limiting factor when GPU compute is otherwise fast enough. This is a direct application of the general performance principle of reducing idle time by overlapping I/O with computation.

## Prerequisites
- [[llm-training-optimization]] — Data preloading reduces GPU idle time during training
- [[gpu-memory-hierarchy]] — Understanding host-to-device transfer overhead motivates preloading

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[llm-training-optimization]]
- [[batch-size]]
- [[large-language-models]]
