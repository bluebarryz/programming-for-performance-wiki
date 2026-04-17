---
tags:
  - concept
  - ece459
  - gpu
  - llm
prerequisites:
  - "[[cuda]]"
  - "[[gpu-memory-hierarchy]]"
  - "[[data-parallelism]]"
---

# Large Language Models

Large language models (LLMs) are trained on massive amounts of text data and can generate human-like text, answer questions, and complete language-related tasks. ChatGPT popularized the conversational variant in November 2022. The "PT" in GPT stands for pre-training on a very large data set (specifically, a lot of text from the internet). These models are relevant to a performance course because generating or updating a pre-trained model is computationally challenging.

A key factor in model quality is the number of parameters. More parameters means a larger, more complex model that can process more data, learn more, and generate better output. However, more parameters also means more computational and memory resources, and more potential for overfitting or underfitting. Parameters are updated during training by an optimization algorithm that minimizes the error between predicted and actual outputs.

The connection to this course is the configuration space for training: there are many knobs to tweak (batch size, gradient accumulation, precision, checkpointing) and performance must be measured against useful metrics, not just "number goes up." The three main groups of optimizations for Transformer-based LLMs are Tensor Contractions (matrix-matrix multiplications, the most computationally intensive), Statistical Normalizations (mapping and reduction), and Element-Wise Operators (dropout, biases -- not very intensive). Training may be limited by GPU memory rather than compute time.

## Prerequisites
- [[cuda]] — LLM training relies on GPU computation via CUDA
- [[gpu-memory-hierarchy]] — Training is often limited by GPU memory rather than compute
- [[data-parallelism]] — Tensor operations in LLM training are data-parallel workloads

## Lectures

- [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]

## Related Concepts

- [[llm-training-optimization]]
- [[batch-size]]
- [[gradient-accumulation]]
- [[gradient-checkpointing]]
- [[mixed-precision-training]]
- [[data-preloading]]
- [[fp32-vs-fp64]]
