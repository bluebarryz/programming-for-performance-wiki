---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[dynamic-branch-prediction]]"
---

# Two-Bit Saturating Counter

A two-bit saturating counter improves on the 1-bit branch prediction scheme by avoiding the double-misprediction problem. With a 1-bit scheme, a branch that is almost always taken (e.g., TTTTTTNTTTT) gets penalized twice for one anomaly: once when it mispredicts the not-taken, and once when it mispredicts the next taken.

The 2-bit counter works as follows:
- Every taken branch increments the counter; every not-taken decrements it
- "Saturating" means it stays at 11 or 00 rather than overflowing/underflowing
- Counter values 00 or 01 predict "not taken"; values 10 or 11 predict "taken"

This means a single anomalous branch outcome won't flip the prediction -- it takes two consecutive mispredictions to change. With fewer table entries than a 1-bit scheme (at the same size), it achieves about 90% accuracy (~1.38 CPI).

Used in chips from the LLNL S-1 (1977) through the Intel Pentium (1993).

## Prerequisites

- [[dynamic-branch-prediction]] — The 2-bit counter improves on the 1-bit dynamic scheme

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[dynamic-branch-prediction]]
- [[branch-prediction]]
- [[two-level-adaptive-predictor]]
