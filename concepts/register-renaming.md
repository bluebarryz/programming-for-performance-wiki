---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[pipeline-hazards]]"
  - "[[out-of-order-execution]]"
---

# Register Renaming

Register renaming eliminates false data dependencies between instructions. When an assembly instruction reads from register R2, the hardware maps it to a physical register (e.g., RA) behind the scenes. If two pairs of instructions both use R2 but for unrelated purposes, the hardware can map them to different physical registers (RX and RY), allowing both pairs to execute in parallel.

For example, given:
```
MOV R2, R7 + 32
ADD R1, R2
MOV R2, R9 + 64
ADD R3, R2
```
Without renaming, instruction 3 must wait for instruction 2 because both use R2. With renaming, the first two instructions use RX and the second two use RY, so they can execute in parallel or at least without stalling.

Register renaming also has synergy with [[branch-prediction]]: speculative changes go into one set of registers while the "old" values are kept in another, enabling better recovery from mispredictions.

## Prerequisites

- [[pipeline-hazards]] — Register renaming eliminates false data hazards
- [[out-of-order-execution]] — Renaming enables more instructions to execute out of order

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[instruction-level-parallelism]]
- [[out-of-order-execution]]
- [[speculation]]
- [[pipeline-hazards]]
