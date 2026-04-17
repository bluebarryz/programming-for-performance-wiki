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

# Likely/Unlikely Hints

Compilers like `gcc` support hints that tell the branch predictor whether a condition is likely or unlikely. In Rust, this is an experimental feature via `core_intrinsics` (`likely()` and `unlikely()` functions), requiring nightly builds and `#![feature(core_intrinsics)]`.

The course tests these hints with a Rust program that iterates over a large vector checking conditions. The results show hints provide no benefit and are marginally worse:

- No hint: 6.657s
- `likely()`: 6.762s
- `unlikely()`: 6.943s

The conclusion: the compiler and CPU branch prediction routines are already very smart. Hints are not always beneficial even when correct, and getting them wrong adds a penalty. Under most circumstances, it is best to leave branch prediction to the hardware unless you are really, really sure.

## Prerequisites

- [[branch-prediction]] — Hints attempt to assist the hardware branch predictor
- [[static-branch-prediction]] — Hints are a form of compile-time static prediction guidance

## Lectures

- [[L07-CPU-Hardware-Branch-Prediction]]

## Related Concepts

- [[branch-prediction]]
- [[static-branch-prediction]]
