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

# Induction Variable Elimination

A loop induction variable varies on each iteration of the loop. A `for` loop variable is a primary induction variable, but there may be others that are functions of it. Induction variable elimination finds and removes these extra variables, simplifying the loop body.

For example, if `s = x * y` is recomputed every iteration but `x` and `y` don't change inside the loop, the multiplication can be hoisted out (see [[loop-invariant-code-motion-aka-hoisting]]). If a secondary variable like `j = 2*i` exists alongside the primary `i`, the compiler can eliminate `j` and compute its value from `i` directly.

## Example

```rust
// Before: j is a secondary induction variable (always 2*i)
for i in 0..100 {
    j = 2 * i;
    a[j] = i;
}

// After: j eliminated, expression inlined
for i in 0..100 {
    a[2 * i] = i;
}
```

## vs. Loop-Invariant Code Motion (Hoisting)

Both optimizations reduce work inside loops, but they target different patterns:

| | Hoisting | Induction Variable Elimination |
|---|---|---|
| **Target** | Value that never changes across iterations | Value that changes, but predictably (linear function of loop counter) |
| **Action** | Move computation before the loop | Remove the redundant variable, derive it from the primary induction variable |
| **Example** | `s = x * y` hoisted out when `x`, `y` are loop-invariant | `j = 2*i` eliminated; use `2*i` directly |

## Prerequisites

- [[loop-optimizations]] — Induction variable elimination is a specific loop optimization technique

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[loop-optimizations]]
- [[loop-invariant-code-motion-aka-hoisting]]
- [[scalar-replacement]]
