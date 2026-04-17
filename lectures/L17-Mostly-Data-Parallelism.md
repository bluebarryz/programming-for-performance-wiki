---
tags:
  - lecture
  - ece459
  - performance
  - parallelism
  - simd
lecture: 17
title: Mostly Data Parallelism
prerequisite_lectures:
  - "[[L06-Modern-Processors]]"
---

# L17 - Mostly Data Parallelism

This lecture distinguishes data parallelism (same operation on many data items) from task parallelism (different operations on different items). It motivates using smaller data types to process more elements per instruction, then introduces SIMD (Single Instruction Multiple Data) as the hardware-supported way to do this. The lecture covers SSE/AVX instruction sets, automatic vectorization by the Rust/LLVM compiler, explicit SIMD via the `simdeez` crate, and a detailed case study of Stream VByte -- a SIMD-accelerated variable-byte integer decoding scheme used in inverted indexes.

## Prerequisite Lectures
- [[L06-Modern-Processors]] — Processor architecture needed to understand SIMD instruction sets and vector registers

## Concepts Covered

- [[data-parallelism]]
- [[task-parallelism]]
- [[simd]]
- [[sse-and-avx]]
- [[auto-vectorization]]
- [[data-layout-and-alignment]]
- [[stream-vbyte]]
- [[inverted-indexes]]
- [[vbyte-encoding]]
