---
tags:
  - concept
  - ece459
  - L13
  - parallelism
  - speculation
prerequisites:
  - "[[speculative-execution]]"
  - "[[dependencies-in-parallelism]]"
---

# Value Speculation

Value speculation breaks a true dependency between a computation and its successor by predicting the result of the first computation and speculatively executing the second based on that prediction. If the prediction is correct, the speculative result is used; otherwise, the second computation is re-run with the actual value.

Example: if `second_long_calculation` depends on the output of `long_calculation`, but the output is predictable (e.g., 90% of the time it's the same value), you can speculatively compute the second function using the predicted value in parallel:

- Original time: `T = T1 + T2`
- Speculative time: `Ts = max(T1, T2) + S + p * T2` (p = probability of misprediction)

This is similar to memoization but with parallelization. It works well when values are predictable (as most values in programs are). Examples include assuming a customer uses a standard billing plan, or using a software cache of a rarely-changing database value.

## Prerequisites

- [[speculative-execution]] — Value speculation is a specific form of speculative execution
- [[dependencies-in-parallelism]] — Value speculation breaks true data dependencies

## Lectures

- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[speculative-execution]]
- [[dependencies]]
