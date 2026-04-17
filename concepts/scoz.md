---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "28"
prerequisites:
  - "[[coz-profiler]]"
  - "[[virtual-speedup]]"
---

# SCoz

SCoz (System-wide Causal Profiler) is an extension of the [[coz-profiler]] that addresses two key limitations: the inability to profile multi-process applications and the inability to account for OS kernel bottlenecks. It was developed by Ahn, Kim, Nam, and Jeong and published in Software: Practice and Experience (2021).

The fundamental change from Coz to SCoz is moving from a thread-based to a core-based approach for virtual speedups. Where Coz pauses all other threads to simulate speeding up a code region, SCoz pauses execution on all other cores. This allows it to capture the impact of kernel code and multi-process interactions. Special care is taken to handle idle cores correctly, ensuring delays are charged to the right core when one is woken up by another.

The implementation uses one profiler thread pinned to each core, whose primary purpose is to call the `ndelay` interface (with preemption temporarily disabled) to stop execution on that specific core. Because SCoz operates within the kernel, it can profile scenarios that user-space tools like Coz cannot reach, but this also imposes limitations on where and how it can be deployed. This kernel-level requirement represents an interesting tradeoff between capability and accessibility.

## Prerequisites

- [[coz-profiler]] — SCoz extends Coz to address its limitations with multi-process and kernel profiling
- [[virtual-speedup]] — SCoz uses a core-based variant of virtual speedup

## Lectures
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts
- [[coz-profiler]]
- [[causal-profiling]]
- [[virtual-speedup]]
