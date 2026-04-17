---
tags:
  - concept
  - ece459
  - L11
  - concurrency
  - thread-safety
prerequisites:
  - "[[data-races]]"
  - "[[parallelism]]"
---

# Reentrancy

A function is reentrant if it can be safely called again while a previous invocation is still in progress (e.g., due to interrupts or concurrent threads). A function is non-reentrant if it depends on global or shared mutable state that changes across invocations.

Classic non-reentrant example (C):
```c
int tmp;
void swap(int x, int y) {
    tmp = y; y = x; x = tmp;
}
```
Moving `tmp` inside the function makes it reentrant, since each invocation has its own copy.

Reentrancy is critical in interrupt service routines (ISRs), which can be interrupted by higher-priority interrupts and restarted. Rust's ownership model discourages the global mutable state that causes reentrancy issues, and requires mutable references to be explicitly annotated.

Reentrant functions are closely related to [[pure-functions]] -- pure functions are always reentrant and thread-safe.

## Prerequisites

- [[data-races]] — Understanding how shared mutable state causes concurrency bugs
- [[parallelism]] — Understanding why reentrant functions matter for concurrent execution

## Lectures

- [[L11-Use-of-Locks-Reentrancy]]

## Related Concepts

- [[pure-functions]]
- [[side-effects]]
- [[functional-programming-and-parallelization]]
