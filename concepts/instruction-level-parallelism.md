---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[pipelining]]"
  - "[[parallelism]]"
---

# Instruction-Level Parallelism

Instruction-Level Parallelism (ILP) is the idea of doing more work in each clock cycle, rather than having more cycles. ILP encompasses several hardware techniques that work synergistically:

- [[pipelining]] -- overlapping instruction stages
- [[out-of-order-execution]] -- executing instructions as their operands become available, not in program order
- [[register-renaming]] -- eliminating false data dependencies
- [[speculation]] -- executing instructions before knowing if they're needed
- [[dual-issue]] -- starting multiple independent instructions simultaneously
- [[branch-prediction]] -- guessing branch outcomes to keep the pipeline full

ILP is approaching its limits as one of the "four walls" of processor performance. Even with near-perfect branch prediction (95%), the marginal gains from further improvement are small. The x86 approach maximizes dynamic (run-time) parallelism, in contrast to Intel's failed Itanium which tried static (compile-time) parallelism.

## Prerequisites

- [[pipelining]] — ILP builds on pipelining as its most fundamental technique
- [[parallelism]] — ILP is the hardware-level application of parallelism within a single core

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[pipelining]]
- [[out-of-order-execution]]
- [[register-renaming]]
- [[speculation]]
- [[branch-prediction]]
- [[dual-issue]]
