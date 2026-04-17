---
tags:
  - concept
  - ece459
  - runtime-optimization
  - concurrency
lectures:
  - L20
prerequisites:
  - "[[escape-analysis]]"
  - "[[jit-compilation]]"
  - "[[mutex]]"
  - "[[lock-contention]]"
---

# Lock Elision and Coarsening

Lock elision and lock coarsening are JIT compiler optimizations enabled by [[escape-analysis]] that reduce the overhead of synchronization in JVM languages.

Lock elision removes a lock entirely when the JIT compiler can determine it serves no purpose. For example, a method or block marked as `synchronized` that can only ever be called from one thread at a time needs no lock at all, eliminating all setup and acquisition costs. Lock coarsening merges sequential synchronized blocks that share the same lock into a single larger synchronized block, reducing the total number of lock/unlock operations. This is pure overhead reduction. A related optimization handles nested locking: if the same lock is acquired repeatedly without releasing (as in recursive code), the redundant acquisitions can be combined so that the overhead of repeated locking and unlocking is avoided.

These optimizations are particularly valuable because they are difficult to perform at compile time. The compiler cannot always determine how many threads will access a given object or what the runtime calling patterns will be. The JIT compiler, however, observes the actual execution and can make these transformations with confidence. This is one of the key advantages of [[jit-compilation]] -- decisions that would require conservative assumptions at compile time can be made aggressively at runtime.

## Prerequisites

- [[escape-analysis]] — Lock elision and coarsening are enabled by escape analysis determining object visibility
- [[jit-compilation]] — These optimizations are performed by the JIT compiler at runtime
- [[mutex]] — Understanding mutex/lock overhead is necessary to appreciate why elision and coarsening help
- [[lock-contention]] — Lock contention motivates the need for these optimizations

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[escape-analysis]]
- [[jit-compilation]]
- [[on-stack-replacement]]
