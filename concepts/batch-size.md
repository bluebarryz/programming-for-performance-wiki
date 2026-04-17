---
tags:
  - concept
  - ece459
  - llm
  - gpu
prerequisites:
  - "[[llm-training-optimization]]"
  - "[[large-language-models]]"
---

# Batch Size

Batch size is the number of training samples the GPU processes at once during LLM training. It is the simplest optimization knob to adjust, analogous to increasing the number of worker threads -- more work per step, but with diminishing returns and potential resource conflicts.

Increasing batch size improves throughput (samples/second) and GPU utilization but consumes more memory. In the course experiments with bert-base-uncased, increasing batch size from 1 to 8 improved throughput from 4.67 to 7.68 samples/second and GPU utilization from 43.1% to 92.9%, but memory usage grew from 3281 MB to 7069 MB. A batch size of 9 caused an out-of-memory error. Binary search is an effective way to find the maximum batch size for a given GPU.

There is no magic number for the ideal batch size. Larger batch sizes can cause the model to overfit or get stuck at local minima, while smaller sizes may underfit. The Yelp training example showed worse accuracy with batch size 1 than 4, and 4 was worse than 8. Training and validation data are essential for finding the right balance.

## Prerequisites
- [[llm-training-optimization]] — Batch size is the simplest training optimization knob
- [[large-language-models]] — Batch size directly affects LLM training throughput and memory

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[llm-training-optimization]]
- [[gradient-accumulation]]
- [[large-language-models]]
