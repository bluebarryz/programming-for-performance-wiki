---
tags:
  - concept
  - ECE459
  - L01
  - L02
  - L03
  - concurrency
prerequisites:
  - "[[parallelism]]"
---

# Data Races

A data race occurs when two threads or processes both attempt to simultaneously access the same data, and at least one of the accesses is a write. This can lead to nonsensical intermediate states becoming visible to one of the participants. Avoiding data races requires coordination between participants to ensure that intermediate states never become visible (typically using locks).

In Rust, the ownership and borrowing system prevents data races at compile time. Immutability by default means "no writes means no races." The borrow checker enforces that you can have either one mutable reference or many immutable references, but not both simultaneously. Rust prevents data races on shared memory locations, though you can still race on the filesystem or other external resources.

Data races are one of the two specific problems (along with [[deadlocks]]) highlighted as complications of parallelism.

## Prerequisites
- [[parallelism]] — Data races arise from concurrent access in parallel execution

## Lectures

- [[L01-Programming-for-Performance]]
- [[L02-Rust-Basics]]
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts

- [[parallelism]]
- [[deadlocks]]
- [[fearless-concurrency]]
- [[immutability-by-default]]
- [[borrow-checker]]
- [[mutex]]
