---
tags:
  - concept
  - ece459
  - hardware
  - L07
prerequisites:
  - "[[two-bit-saturating-counter]]"
  - "[[dynamic-branch-prediction]]"
---

# Two-Level Adaptive Predictor

Two-level adaptive predictors improve accuracy by using branch history patterns to make predictions. They come in two variants:

**Global**: Store the last few branch outcomes (e.g., 3 bits of history) and use these to index into a table of [[two-bit-saturating-counter|two-bit saturating counters]]. The history captures patterns like a `for (int i = 0; i < 3; ++i)` loop which follows a TTN pattern. For example, after seeing TTT, predict N; after TTN, predict T. This achieves about 93% accuracy (~1.27 CPI). The Pentium MMX (1996) used a 4-bit global branch history.

**Local**: Instead of one global history, keep a separate history for each branch. The branch address determines which history to use, and the history concatenated with the address indexes into the counter table. This captures per-branch patterns better, achieving about 94% accuracy (~1.23 CPI). Used in Pentium Pro (1996), Pentium II (1997), and Pentium III (1999).

The diminishing returns are notable: each improvement yields a smaller gain, but the cumulative effect is significant.

## Prerequisites

- [[two-bit-saturating-counter]] — Two-level predictors use tables of 2-bit saturating counters
- [[dynamic-branch-prediction]] — Two-level predictors are a more sophisticated dynamic scheme

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[dynamic-branch-prediction]]
- [[two-bit-saturating-counter]]
- [[gshare-predictor]]
- [[branch-prediction]]
