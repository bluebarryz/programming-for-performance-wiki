---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[branch-prediction]]"
  - "[[static-branch-prediction]]"
---

# Dynamic Branch Prediction

Dynamic branch prediction uses runtime execution history to predict future branch outcomes. This is important when program execution has distinct phases with distinct branch behaviors.

**1-bit scheme**: Record whether each branch was taken or not last time. Use the low bits of the branch address as an index into a table. This introduces aliasing (different branches mapping to the same table entry). Achieves about 85% accuracy (~1.57 CPI). Used in DEC EV4 (1992) and MIPS R8000 (1994).

**[[two-bit-saturating-counter]]**: Stores whether a branch is "usually" taken using a 2-bit counter, avoiding double penalties from occasional mispredictions. ~90% accuracy (~1.38 CPI).

**[[two-level-adaptive-predictor]]**: Uses recent branch history (global or per-branch) to index into a table of 2-bit counters, capturing patterns like loop iteration counts. ~93-94% accuracy.

**[[gshare-predictor]]**: XORs branch address and history (instead of concatenating) to use more bits efficiently. Same accuracy, simpler design.

## Prerequisites

- [[branch-prediction]] — Dynamic prediction improves on static schemes by using runtime history
- [[static-branch-prediction]] — Dynamic schemes are motivated by the limitations of static approaches

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[branch-prediction]]
- [[static-branch-prediction]]
- [[two-bit-saturating-counter]]
- [[two-level-adaptive-predictor]]
- [[gshare-predictor]]
