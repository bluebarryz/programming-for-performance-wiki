---
tags:
  - lecture
  - ece459
  - locking
  - reentrancy
  - parallelism
lecture: L11
title: "Use of Locks, Reentrancy"
prerequisite_lectures:
  - "[[L09-Algorithms-Concurrency-and-Parallelism]]"
---

# L11 -- Use of Locks, Reentrancy

This lecture covers how to use locks effectively for performance, not just correctness. Critical sections should be as small as possible -- containing only the shared accesses that truly need protection. The lecture discusses the trade-offs between coarse-grained and fine-grained locking (overhead, contention, deadlocks), deadlock avoidance strategies (consistent lock ordering, trylock), and the concept of reentrancy. It concludes with how functional programming and pure functions lend themselves to parallelization, and how Rust nudges programmers toward these patterns.

## Prerequisite Lectures
- [[L09-Algorithms-Concurrency-and-Parallelism]] — Locking, synchronization, and parallelization concepts this lecture builds on

## Concepts Covered

- [[critical-section-sizing]]
- [[locking-granularity]]
- [[coarse-grained-locking]]
- [[fine-grained-locking]]
- [[lock-overhead]]
- [[lock-contention]]
- [[deadlock]]
- [[trylock]]
- [[reentrancy]]
- [[pure-functions]]
- [[side-effects]]
- [[functional-programming-and-parallelization]]
- [[global-interpreter-lock]]
