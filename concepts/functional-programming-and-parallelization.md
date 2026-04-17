---
tags:
  - concept
  - ece459
  - L11
  - functional-programming
  - parallelism
prerequisites:
  - "[[parallelism]]"
  - "[[dependencies-in-parallelism]]"
---

# Functional Programming and Parallelization

Purely functional programming languages (e.g., Haskell, Scala) lend themselves to parallelization because purely functional programs have no [[side-effects]] and are thus trivially parallelizable. If a function is impure, its signature will indicate so.

As Joel Spolsky noted, MapReduce -- the algorithm behind Google's scalability -- comes directly from functional programming concepts (Map and Reduce from Lisp). It works because purely functional programs have no side effects.

The key insight is to write code like mathematical functions: `f(x, y, z) -> (a, b, c)`. This requires that there be no data dependency between functions. Object-oriented programming habits (void methods, mutation through side effects) work against this goal.

Rust encourages functional-style programming by discouraging mutability, encouraging immutable references or ownership transfer, and making internal mutability explicit.

## Prerequisites

- [[parallelism]] — Understanding the goal of running computations concurrently
- [[dependencies-in-parallelism]] — Understanding how data dependencies block parallelization

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[pure-functions]]
- [[side-effects]]
- [[reentrancy]]
