---
tags:
  - lecture
  - ece459
  - performance
  - compiler
  - optimization
lecture: 18
title: Compiler Optimizations
prerequisite_lectures:
  - "[[L06-Modern-Processors]]"
  - "[[L13-Dependencies-and-Speculation]]"
---

# L18 - Compiler Optimizations

This lecture surveys representative compiler optimizations and how they improve performance. It covers scalar optimizations (constant folding, common subexpression elimination, constant/copy propagation, dead code elimination), loop optimizations (induction variable elimination, scalar replacement, loop unrolling, loop interchange, loop fusion/fission, loop-invariant code motion), low-level optimizations (cold attributes, architecture-specific codegen), interprocedural analysis (alias/pointer analysis, call graphs, devirtualization, inlining, tail recursion elimination), and link-time optimizations (LTO) for whole-program optimization.

## Prerequisite Lectures
- [[L06-Modern-Processors]] — Pipelining and ILP needed to understand why loop and instruction-level optimizations matter
- [[L13-Dependencies-and-Speculation]] — Dependencies needed to understand what limits compiler reordering and optimization

## Concepts Covered

- [[compiler-optimization-levels]]
- [[constant-folding]]
- [[common-subexpression-elimination]]
- [[constant-propagation]]
- [[copy-propagation]]
- [[dead-code-elimination]]
- [[loop-optimizations]]
- [[induction-variable-elimination]]
- [[scalar-replacement]]
- [[loop-unrolling]]
- [[loop-interchange]]
- [[loop-fusion-and-fission]]
- [[loop-invariant-code-motion-aka-hoisting]]
- [[alias-and-pointer-analysis]]
- [[call-graphs]]
- [[devirtualization]]
- [[inlining]]
- [[tail-recursion-elimination]]
- [[link-time-optimization]]
