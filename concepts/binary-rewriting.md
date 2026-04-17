---
tags:
  - concept
  - ece459
  - runtime-optimization
lectures:
  - L20
prerequisites:
  - "[[compiler-optimization-levels]]"
  - "[[jit-compilation]]"
  - "[[observe-and-change]]"
---

# Binary Rewriting

Binary rewriting is the technique of modifying a program's compiled machine code at runtime to improve performance. In languages like C or Rust that lack a managed runtime (unlike the JVM), binary rewriting requires explicit effort -- either by preparing multiple compiled variants at build time or by invoking a compiler at runtime.

One approach is to compile several variants of the same code section with different optimization decisions at build time, then swap in the best variant based on observed runtime behavior. A more dynamic approach takes the binary code of a hot segment, feeds it to a compiler on the target system (e.g., LLVM or gcc), which converts it to intermediate representation, optimizes with runtime information, and recompiles. Research by Engelke, Hildenbrand, and Schulz (2019) demonstrated significant speedups on matrix computations using this technique, though the recompilation itself has a non-trivial cost that must be amortized over many executions.

A practical concern is that programs that modify their own binary code are frequently flagged as suspicious by anti-virus and anti-malware software, since self-modifying code is a technique historically used by viruses to evade detection. This is worth considering when shipping to end-user systems.

## Prerequisites

- [[compiler-optimization-levels]] — Binary rewriting re-applies compiler optimizations at runtime with additional information
- [[jit-compilation]] — Binary rewriting is an alternative to JIT for languages without a managed runtime
- [[observe-and-change]] — Binary rewriting uses observed runtime behavior to guide recompilation decisions

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[jit-compilation]]
- [[on-stack-replacement]]
- [[observe-and-change]]
- [[intrinsics]]
