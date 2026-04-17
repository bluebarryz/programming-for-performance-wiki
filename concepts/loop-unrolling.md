---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[loop-optimizations]]"
  - "[[branch-prediction]]"
  - "[[simd]]"
---

# Loop Unrolling

Loop unrolling replaces a loop with repeated inline copies of the loop body, reducing branch overhead from the loop condition check.

Example:
```
for i in &[1,2,3,4] { f(*i); }   =>   f(0); f(1); f(2); f(3);
```

This lets the processor run more code without branching as often. It also enables *software pipelining*, a synergistic optimization that allows multiple iterations to proceed in parallel. Loop unrolling is also useful for [[simd]] because it exposes more data-level parallelism to the vectorizer.

Rust does this automatically at appropriate optimization levels.

## Prerequisites

- [[loop-optimizations]] — Loop unrolling is a specific loop optimization technique
- [[branch-prediction]] — Unrolling reduces branch overhead from loop condition checks
- [[simd]] — Unrolling exposes more data-level parallelism to the vectorizer

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-optimizations]]
- [[simd]]
- [[auto-vectorization]]
- [[loop-interchange]]
