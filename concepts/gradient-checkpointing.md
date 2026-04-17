---
tags:
  - concept
  - ece459
  - llm
  - gpu
prerequisites:
  - "[[llm-training-optimization]]"
  - "[[batch-size]]"
---

# Gradient Checkpointing

Gradient checkpointing trades compute time for reduced memory usage during LLM training. By default, all activations from the forward pass are saved so they can be used in the backward pass. Gradient checkpointing saves only some activations and recomputes the rest from scratch during the backward pass.

The memory savings can be significant: with batch size 8 and no gradient accumulation, enabling checkpointing reduced memory from 7069 MB to 3619 MB (roughly half), but training time increased from 66.70s to 93.07s (about 40% slower). The freed memory can then be used to increase the batch size -- raising it to 16 with checkpointing used 3731 MB and took 100.55s. However, the time increase from checkpointing may not be offset by larger batch sizes, and excessively large batch sizes can make training quality worse. The approach could not save the larger bert-large-uncased model from OOM on the limited test hardware.

## Prerequisites
- [[llm-training-optimization]] — Checkpointing is a memory-saving technique for training
- [[batch-size]] — Freed memory from checkpointing can be used to increase batch size

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[llm-training-optimization]]
- [[batch-size]]
- [[gradient-accumulation]]
- [[mixed-precision-training]]
