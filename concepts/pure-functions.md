---
tags:
  - concept
  - ece459
  - L11
  - functional-programming
  - parallelism
prerequisites:
  - "[[parallelism]]"
  - "[[data-races]]"
---

# Pure Functions

A function is pure if it has no [[side-effects]] and its outputs depend solely on its inputs. Pure functions are inherently thread-safe and reentrant, making them trivially parallelizable.

Rust nudges programmers toward pure-function style by discouraging mutability and requiring explicit annotation of mutable references. Writing code as mathematical functions `f(x, y, z) -> (a, b, c)` avoids the hidden dependencies that come from side effects.

Object-oriented programming encourages `void` methods that operate through side effects, which is the opposite of the functional approach and makes parallelization harder.

## Prerequisites

- [[parallelism]] — Understanding why thread-safe functions enable parallelization
- [[data-races]] — Understanding the shared-state problems pure functions avoid

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[reentrancy]]
- [[side-effects]]
- [[functional-programming-and-parallelization]]
