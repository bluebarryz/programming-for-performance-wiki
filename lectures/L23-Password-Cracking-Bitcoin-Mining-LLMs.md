---
tags:
  - lecture
  - ece459
  - gpu
  - security
  - cryptography
  - llm
lecture: L23
title: Password Cracking, Bitcoin Mining, LLMs
prerequisite_lectures:
  - "[[L21-GPU-Programming]]"
  - "[[L22-GPU-Programming-Continued]]"
---

# L23 - Password Cracking, Bitcoin Mining, LLMs

This lecture explores three GPU application domains. First, password cracking: proper password storage uses cryptographic hashing (not plaintext), and GPUs excel at brute-forcing hashes. The scrypt algorithm counters this by being memory-hard, making cracking expensive in both time and space. Rainbow tables offer a time-space tradeoff for precomputing hash chains. Second, Bitcoin mining evolved from CPUs to GPUs to FPGAs to ASICs due to increasing difficulty of SHA-256 computations. Third, large language models (LLMs) rely on GPUs for training via tensor contractions, statistical normalizations, and element-wise operators. The lecture covers LLM training optimizations including batch size tuning, gradient accumulation, gradient checkpointing, mixed precision, and data preloading.

## Prerequisite Lectures
- [[L21-GPU-Programming]] — GPU programming model needed to understand why GPUs excel at brute-force and training workloads
- [[L22-GPU-Programming-Continued]] — Kernel launching and device management needed for practical GPU application context

## Concepts Covered

- [[password-cracking]]
- [[cryptographic-hashing]]
- [[scrypt]]
- [[memory-hard-functions]]
- [[rainbow-tables]]
- [[bitcoin-mining]]
- [[asic-miners]]
- [[large-language-models]]
- [[llm-training-optimization]]
- [[batch-size]]
- [[gradient-accumulation]]
- [[gradient-checkpointing]]
- [[mixed-precision-training]]
- [[data-preloading]]
