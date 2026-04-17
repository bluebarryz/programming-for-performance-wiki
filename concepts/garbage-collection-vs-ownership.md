---
tags:
  - concept
  - ECE459
  - L02
  - rust
  - performance
prerequisites:
  - "[[ownership]]"
  - "[[rust-memory-management]]"
---

# Garbage Collection vs Ownership

Garbage collection is well-understood and convenient, but has two performance costs: the runtime overhead of tracking allocations, and the collection cost itself (stop-the-world pauses, memory reorganization, unpredictable timing).

The lecture presents a real-world case study: **Discord switching from Go to Rust**. Go's garbage collector caused large latency spikes. Rust, using ownership, immediately frees memory when it is no longer needed -- no waiting for a collector. C++ with RAII would also avoid GC spikes. The Rust version outperformed Go in latency, CPU usage, and memory usage.

GC is still handy for certain data structures (graphs, doubly-linked lists) where ownership cycles are natural. Many Rust people argue you shouldn't use linked lists for performance anyway. Alternatively, you can use `unsafe` Rust or [[rc-reference-counting]] for shared ownership (which can leak memory if cycles form).

## Prerequisites
- [[ownership]] — The comparison requires understanding Rust's ownership model
- [[rust-memory-management]] — GC vs ownership is a memory management strategy comparison

## Lectures

- [[L02-Rust-Basics]]

## Related Concepts

- [[ownership]]
- [[rust-memory-management]]
- [[raii]]
- [[rc-reference-counting]]
