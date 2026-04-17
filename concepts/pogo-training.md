---
tags:
  - concept
  - ece459
  - pogo
  - methodology
lectures:
  - L27
prerequisites:
  - "[[profile-guided-optimization]]"
  - "[[pogo-probes]]"
---

# POGO Training

The training phase of [[profile-guided-optimization|POGO]] involves running the instrumented executable through real-world scenarios. Key principles:

- Focus training time on **performance-critical sections**
- Use **realistic workloads** that match actual usage patterns
- Do NOT try to exercise every feature (this is not unit testing) -- doing so teaches the compiler that everything is equally important, which is counterproductive
- Multiple training runs can be combined, and runs can be **merged with user-assigned weightings** to emphasize important scenarios
- The `.profraw` output files need processing with `llvm-profdata merge` before recompilation

The program runs much slower during training due to the overhead of the inserted [[pogo-probes|probes]].

## Prerequisites

- [[profile-guided-optimization]] — Training is the second phase of the POGO workflow
- [[pogo-probes]] — Training runs the instrumented binary that contains probes

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[profile-guided-optimization]]
- [[pogo-probes]]
- [[pogo-optimizations]]
