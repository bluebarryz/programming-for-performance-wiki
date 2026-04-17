---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[cache-misses]]"
  - "[[out-of-order-execution]]"
  - "[[speculation]]"
---

# Miss Shadow

When a load instruction misses the cache, the hardware tracks that the target register is "not quite ready yet" and continues executing subsequent instructions that don't depend on that register. The useful work done during the wait for the cache miss to resolve is called the "miss shadow."

It is possible to have more than one load in flight at a time (two or more on various CPU architectures). This means the processor can overlap multiple cache misses, significantly reducing the effective penalty. The goal is to start the next cache miss as soon as possible so it overlaps with the current one -- the sooner it starts, the sooner it finishes, and the faster the program runs.

This is one of the key benefits of [[out-of-order-execution]] and [[speculation]]: they allow the processor to look ahead past a cache miss and find more independent work (including other loads that may also miss).

## Prerequisites

- [[cache-misses]] — Miss shadow is the useful work done while waiting for a cache miss to resolve
- [[out-of-order-execution]] — OOO execution enables work during the miss shadow by finding independent instructions
- [[speculation]] — Speculation allows looking past a miss to discover more independent work

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[cache-misses]]
- [[out-of-order-execution]]
- [[speculation]]
- [[instruction-level-parallelism]]
