---
tags:
  - concept
  - ece459
  - hardware
  - L01
  - L06
  - L07
prerequisites:
  - "[[bandwidth-vs-latency]]"
  - "[[parallelism]]"
---

# Pipelining

A key concept for parallelism. All modern CPUs use pipelining, but you can also apply it in your code. Think of an assembly line: you split a task into a set of subtasks and execute these subtasks in parallel (L01).

At the hardware level, a single instruction goes through five stages: (1) fetch from memory, (2) decode, (3) fetch operands, (4) execute, and (5) write result. Without pipelining, instruction 2 cannot start until instruction 1 finishes all five stages. With pipelining, instruction 2 can begin its fetch while instruction 1 is being decoded, so ideally one instruction completes per clock cycle.

Pipelining does not reduce the latency of a single instruction -- it increases throughput by keeping all stages busy simultaneously. Modern pipelines are much longer than five stages, which increases throughput but also increases the cost of mispredictions (more work must be thrown away).

Pipelining is a prerequisite for [[branch-prediction]] -- the longer the pipeline, the more important it is to predict branches correctly to avoid flushing speculative work.

## Prerequisites

- [[bandwidth-vs-latency]] — Pipelining improves throughput (bandwidth) without reducing single-instruction latency
- [[parallelism]] — Pipelining is a form of parallelism applied at the instruction level

## Lectures

- [[L01-Programming-for-Performance]]
- [[L06-Modern-Processors]]
- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[parallelism]]
- [[embarrassingly-parallel]]
- [[bandwidth-vs-latency]]
- [[pipeline-hazards]]
- [[branch-prediction]]
- [[instruction-level-parallelism]]
- [[dual-issue]]
