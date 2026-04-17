---
tags:
  - concept
  - ece459
  - L13
  - parallelism
  - speculation
prerequisites:
  - "[[parallelism]]"
  - "[[dependencies-in-parallelism]]"
  - "[[branch-prediction]]"
---

# Speculative Execution

Speculative execution starts a computation that may or may not be needed, in parallel with the computation that determines whether it is needed. If the speculation is correct, time is saved; if wrong, the speculative work is discarded.

Example: if `second_long_calculation(x, y)` might be needed based on the result of `long_calculation(x, y)`, and the two share no dependencies, you can run both in parallel:

- Original time: `T = T1 + p * T2` (where p is the probability the second calc is needed)
- Speculative time: `Ts = max(T1, T2) + S` (S = synchronization overhead)

Speculation is profitable when the probability of needing the result is high and the synchronization overhead is low relative to the savings.

This is analogous to CPU branch prediction, where the processor speculatively executes a branch target and rolls back if the prediction was wrong.

Conditions for safe speculation:
- The functions must not call each other
- The speculated function must not depend on values set by the first
- The first function's return value must be deterministic
- [[side-effects]] of speculated functions must be considered carefully

## Prerequisites

- [[parallelism]] — Speculation runs computations in parallel to save time
- [[dependencies-in-parallelism]] — Speculation is a technique to work around dependencies
- [[branch-prediction]] — CPU branch prediction is the hardware analogue of speculative execution

## Lectures

- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[value-speculation]]
- [[dependencies]]
- [[side-effects]]
- [[software-transactional-memory]]
