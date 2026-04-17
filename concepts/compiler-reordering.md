---
tags:
  - concept
  - ece459
  - memory-consistency
  - reordering
lectures:
  - L15
prerequisites:
  - "[[instruction-level-parallelism]]"
  - "[[pipelining]]"
  - "[[data-races]]"
---

# Compiler Reordering

Compiler reordering is the optimization where the compiler changes the order of instructions from what the programmer wrote in order to improve performance. The compiler does not simply translate each statement into machine code in sequence; it may rearrange instructions to fill load-delay slots, reduce pipeline stalls, or take advantage of instruction-level parallelism.

For example, if a value `x` is loaded from memory and the next instruction immediately uses it, there may be a stall while waiting for the load to complete. The compiler can move unrelated instructions into that gap to do useful work during the wait. This is generally safe in single-threaded programs because the compiler respects data dependencies within a thread.

The danger arises in concurrent programs. The compiler does not inherently understand cross-thread relationships, so it may reorder a store past a mutex unlock or move an access outside a critical section. If a program has undefined behaviour (such as data races), the compiler is allowed to do anything it wants with reordering. [[memory-barriers]] and atomic operations with appropriate [[memory-consistency-models]] are the tools used to prevent unsafe compiler reorderings.

## Prerequisites

- [[instruction-level-parallelism]] — Compiler reordering exploits ILP to fill pipeline stalls
- [[pipelining]] — Understanding pipeline stalls that motivate instruction reordering
- [[data-races]] — Reordering is dangerous specifically in the presence of data races

## Lectures

- [[L15-Memory-Consistency]]

## Related Concepts

- [[hardware-reordering]]
- [[memory-barriers]]
- [[sequential-consistency]]
- [[memory-consistency-models]]
