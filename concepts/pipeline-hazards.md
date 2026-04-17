---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[pipelining]]"
---

# Pipeline Hazards

Pipeline hazards prevent the processor from reaching the theoretical maximum of one instruction completed per clock cycle. There are three kinds:

1. **Data hazards**: An instruction needs the result of a previous instruction that hasn't finished yet. For example, if instruction 2 reads a register that instruction 1 is still computing.
2. **Structural hazards**: Conflicts over CPU resources, such as two instructions needing the same floating-point unit simultaneously.
3. **Control hazards**: The next instruction cannot be identified because of a branch -- we don't know which path to take until the branch resolves.

In the worst case (a mispredicted branch), the pipeline must be flushed: all speculatively fetched, decoded, and partially executed instructions are thrown away. Techniques like [[register-renaming]], [[out-of-order-execution]], and [[branch-prediction]] exist to mitigate these hazards.

## Prerequisites

- [[pipelining]] — Hazards are the obstacles that prevent pipelining from reaching ideal throughput

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[pipelining]]
- [[branch-prediction]]
- [[register-renaming]]
- [[out-of-order-execution]]
