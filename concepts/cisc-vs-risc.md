---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[pipelining]]"
---

# CISC vs RISC

**CISC** (Complex Instruction Set Computer) processors like x86 have many assembly instructions, designed for programmer convenience. These are easy to program in from the assembly programmer's perspective, but hard to implement in hardware and hard to pipeline. For CISC, Cycles Per Instruction (CPI) varied (e.g., 4-10 cycles) but was predictable.

**RISC** (Reduced Instruction Set Computer) processors have simpler instructions with fewer cycles per instruction, making them easier to scale and pipeline. The tradeoff is that RISC is harder to program in assembly directly, so compilers must do the work. RISC also introduced problems like delay slots, where an instruction after a branch is always executed even if the branch is taken.

Between 1990 and 2005, RISC drove impressive frequency scaling gains. The modern x86 approach tries to get the best of both worlds: a CISC instruction set decoded into simpler micro-ops that are executed in a RISC-like pipeline internally.

## Prerequisites

- [[pipelining]] — RISC designs are easier to pipeline; understanding pipelining is needed to see why RISC matters for performance

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[pipelining]]
- [[frequency-scaling]]
- [[instruction-level-parallelism]]
