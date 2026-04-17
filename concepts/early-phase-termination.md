---
tags:
  - concept
  - ece459
  - performance
  - approximation
lectures:
  - L14
prerequisites:
  - "[[improving-latency]]"
  - "[[parallelism]]"
---

# Early Phase Termination

Early phase termination is a performance strategy where slow or unnecessary tasks are killed or discarded rather than waiting for them to complete. The term comes from Rinard (2007) and applies directly to barrier synchronization: instead of waiting for every thread to reach a barrier, slow threads are terminated so the program can proceed.

This is acceptable when the discarded work does not materially change the result. A statistical model of program behaviour can ensure that killed tasks do not introduce unacceptable distortions, producing an output with a confidence interval. Examples include Monte Carlo simulations (where missing random sample points can be interpolated from neighbours), raytracers (where a missing pixel can be averaged from adjacent ones), and majority-vote protocols (where the outcome is decided before all votes are in).

Early phase termination also applies to optimization problems. For the travelling salesperson problem, you can abandon a partial solution once its accumulated cost exceeds the best known solution. For problems with known bounds like the Rubik's Cube (solvable in at most 20 moves), solution attempts exceeding that bound can be cancelled immediately. The key insight is that "close enough is good enough" -- trading completeness for speed.

## Prerequisites

- [[improving-latency]] — Early termination is a strategy for reducing latency by skipping work
- [[parallelism]] — Applies to barrier synchronization where slow threads are killed

## Lectures

- [[L14-Early-Termination-Reduced-Resource-Computation]]

## Related Concepts

- [[reduced-resource-computation]]
- [[loop-perforation]]
- [[speculation]]
