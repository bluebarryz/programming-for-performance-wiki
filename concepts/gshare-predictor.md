---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[two-level-adaptive-predictor]]"
---

# Gshare Predictor

The gshare predictor is a variant of the [[two-level-adaptive-predictor]]. Instead of concatenating the branch address and history bits to form an index, gshare XORs them. This allows using more bits for both the history and the address within the same table size, simplifying the design while maintaining the same accuracy.

The problem gshare helps with is aliasing: different branches (with different histories) mapping to the same index in the prediction table. By XORing instead of concatenating, gshare spreads entries more evenly across the table.

More sophisticated predictors exist that further reduce aliasing, but the course stops at gshare as the endpoint of the branch prediction progression.

## Prerequisites

- [[two-level-adaptive-predictor]] — Gshare is a variant that XORs instead of concatenating address and history bits

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[dynamic-branch-prediction]]
- [[two-level-adaptive-predictor]]
- [[branch-prediction]]
