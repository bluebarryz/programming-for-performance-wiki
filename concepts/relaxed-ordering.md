---
tags:
  - concept
  - ece459
  - memory-consistency
  - atomics
lectures:
  - L15
prerequisites:
  - "[[atomic-operations]]"
  - "[[sequential-consistency]]"
---

# Relaxed Ordering

Relaxed ordering (`Ordering::Relaxed` in Rust) is the weakest memory ordering for atomic operations. It provides no ordering guarantees at all: the compiler and hardware are free to perform any reordering they wish, including ones that may be surprising or undesirable. The only guarantee is that the operation itself is atomic (no torn reads or writes).

The Rustonomicon suggests that relaxed ordering is appropriate only when the atomic variable is not being used to synchronize any other action. A canonical example is a simple request counter: atomically incrementing a counter for each request to track metrics. It does not matter whether request 9591's increment is visible before or after request 9598's -- the final total will be correct regardless of ordering.

Relaxed ordering should not be used for flags, locks, or any coordination between threads where the order of operations matters. Using it incorrectly can lead to bugs that are extremely difficult to diagnose because they may only manifest on weakly-ordered hardware like ARM and may disappear in debug builds. When in doubt, use [[sequential-consistency]].

## Prerequisites

- [[atomic-operations]] — Relaxed ordering is the weakest ordering for atomic operations
- [[sequential-consistency]] — Understanding the stronger ordering that relaxed forgoes

## Lectures

- [[L15-Memory-Consistency]]

## Related Concepts

- [[acquire-release-ordering]]
- [[sequential-consistency]]
- [[memory-consistency-models]]
- [[atomic-operations]]
