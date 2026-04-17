---
tags:
  - concept
  - ece459
  - L12
  - concurrency
  - atomics
prerequisites:
  - "[[compare-and-swap]]"
---

# ABA Problem

The ABA problem occurs when a value at a memory location is read as A, changed to B by another thread, then changed back to A. A subsequent [[compare-and-swap]] sees A and succeeds (a "false positive"), even though the value was modified in the meantime.

This is dangerous for lock-free data structures because the CAS succeeds despite the underlying data structure having been modified, potentially leading to incorrect behavior.

Example sequence:
1. P1 reads A from location L
2. Pk writes B to L
3. Pj writes A back to L
4. P1 resumes and CAS succeeds -- false positive

Mitigations:
- **Tagging/versioning**: attach a nonce or modification counter to the value, incremented on every write. Double compare-and-swap atomically swaps both value and nonce.
- Java collections use a modification count: iterators check if the count has changed and throw `ConcurrentModificationException` if so.

## Prerequisites

- [[compare-and-swap]] — The ABA problem is a failure mode of CAS operations

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[compare-and-swap]]
- [[lock-free-data-structures]]
- [[atomic-operations]]
