---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[pipelining]]"
  - "[[instruction-level-parallelism]]"
---

# Dual Issue

Dual issue is a hardware capability where the processor starts two consecutive instructions in the same clock cycle. This is possible when the two instructions:

1. Take the same amount of time
2. Use unrelated registers
3. Don't consume two of the same resource (e.g., both needing the same ALU)

For example, `ADD R1, 16` and `CMP R2, 0` do different things with different registers, so they can be fetched/decoded/executed in parallel. In embedded systems with computationally intensive loops (e.g., media encoding/decoding), careful programming can ensure dual issue happens on every cycle.

## Prerequisites

- [[pipelining]] — Dual issue extends pipelining by starting two instructions per cycle
- [[instruction-level-parallelism]] — Dual issue is one of the ILP techniques

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[instruction-level-parallelism]]
- [[pipelining]]
- [[out-of-order-execution]]
