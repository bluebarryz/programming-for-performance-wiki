---
tags:
  - concept
  - ece459
  - L11
  - L13
  - concurrency
  - parallelism
prerequisites:
  - "[[parallelism]]"
  - "[[dependencies-in-parallelism]]"
---

# Side Effects

A side effect is a change in state that does not depend on the function's input, or any visible effect on the outside world beyond the return value. Examples include modifying a global variable, printing to console, or writing to a file.

Side effects are problematic for parallelism because they create hidden dependencies between functions. A function with side effects cannot be safely reordered, duplicated, or run concurrently without risking incorrect results.

Some side effects are unavoidable (e.g., I/O), but others (e.g., modifying global state) can often be eliminated. Rust discourages unnecessary side effects through its ownership model, though atomic types can still represent shared global state.

When considering [[speculative-execution]], side effects must be carefully evaluated -- speculated code with side effects may cause problems if the speculation turns out to be unnecessary.

## Prerequisites

- [[parallelism]] — Understanding why side effects hinder parallel execution
- [[dependencies-in-parallelism]] — Side effects create hidden dependencies between functions

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]
- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[pure-functions]]
- [[reentrancy]]
- [[functional-programming-and-parallelization]]
- [[speculative-execution]]
