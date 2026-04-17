---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[loop-optimizations]]"
---

# Scalar Replacement

Scalar replacement replaces repeated array reads `a[i]` with a single read into a temporary variable `temp = a[i]`, then uses `temp` for subsequent references. This avoids redundant memory accesses.

The compiler needs to know that `a[i]` won't change between reads. This doesn't come up in idiomatic Rust because you would typically iterate using an `IntoIterator` rather than indexing, which naturally avoids repeated lookups.

## Prerequisites

- [[loop-optimizations]] — Scalar replacement is a specific loop optimization that avoids redundant array reads

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-optimizations]]
- [[induction-variable-elimination]]
