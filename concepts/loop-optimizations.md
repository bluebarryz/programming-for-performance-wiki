---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[dependencies-in-parallelism]]"
  - "[[profiling]]"
---

# Loop Optimizations

Loop optimizations are often a big win because programs spend a lot of time looping, especially in loops with high iteration counts. Profiling helps identify which loops are worth optimizing.

Key concepts:
- A **loop induction variable** is a variable that changes on each iteration (e.g., a `for` loop variable). There may be secondary induction variables computable from the primary one.
- **[[induction-variable-elimination]]** finds and removes extra induction variables.
- **[[scalar-replacement]]** replaces repeated array reads `a[i]` with a single `temp = a[i]`.
- Sane languages with bounds checks can have those checks eliminated by loop optimizations when the compiler can prove the loop never exceeds array bounds.

Specific loop transformations include [[loop-unrolling]], [[loop-interchange]], [[loop-fusion-and-fission]], and [[loop-invariant-code-motion-aka-hoisting]].

## Prerequisites

- [[dependencies-in-parallelism]] — Loop optimizations must respect data dependencies between iterations
- [[profiling]] — Profiling identifies which loops are worth optimizing

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-unrolling]]
- [[loop-interchange]]
- [[loop-fusion-and-fission]]
- [[loop-invariant-code-motion-aka-hoisting]]
- [[induction-variable-elimination]]
- [[scalar-replacement]]
- [[auto-vectorization]]
