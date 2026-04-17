---
tags:
  - concept
  - ece459
  - runtime-optimization
lectures:
  - L20
prerequisites:
  - "[[jit-compilation]]"
  - "[[mutex]]"
---

# Escape Analysis

Escape analysis is a runtime optimization performed by the JIT compiler (e.g., in the JVM's HotSpot) to determine whether an object allocated inside a method is visible outside of that method -- that is, whether it "escapes." If an object does not escape, the JIT compiler can apply several optimizations.

The most direct benefit is avoiding heap allocation: non-escaping objects can be stack-allocated instead, which is faster and reduces pressure on the garbage collector. More interesting are the lock optimizations that escape analysis enables. [[lock-elision-and-coarsening|Lock elision]] removes locks entirely when the JIT compiler can prove that a synchronized block is only ever accessed by a single thread. Lock coarsening merges sequential synchronized blocks that share the same lock, reducing the total number of lock/unlock operations. Nested lock optimization combines redundant acquisitions of the same lock in recursive code.

These optimizations are difficult or impossible at compile time because the compiler cannot know the full runtime calling context. The JIT compiler, however, observes actual execution and can make these determinations with confidence. Escape analysis is one of the key advantages that JVM-style runtimes have over ahead-of-time compiled languages like Rust, which make all optimization decisions at compile time.

## Prerequisites

- [[jit-compilation]] — Escape analysis is performed by the JIT compiler at runtime
- [[mutex]] — Understanding locks is needed to appreciate lock elision and coarsening that escape analysis enables

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[jit-compilation]]
- [[lock-elision-and-coarsening]]
- [[on-stack-replacement]]
- [[intrinsics]]
