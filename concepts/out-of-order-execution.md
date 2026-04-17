---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites:
  - "[[pipelining]]"
  - "[[pipeline-hazards]]"
---

# Out-of-Order Execution

Out-of-Order (O-O-O) Execution allows the processor to execute instructions in a different order than they appear in the program, as long as data dependencies are respected. This works synergistically with [[register-renaming]], [[branch-prediction]], and [[speculation]].

The benefit is that the processor can continue doing useful work while waiting for slow operations (like cache misses) to complete, rather than stalling the entire pipeline. If instruction 3 doesn't depend on instructions 1 or 2, it can execute even while instructions 1 and 2 are waiting on memory.

The x86 architecture has been incrementally improved to maximize dynamic (run-time) parallelism through more pipelining, re-order buffers, and additional functional units.

## Prerequisites

- [[pipelining]] — Out-of-order execution reorders instructions within the pipeline
- [[pipeline-hazards]] — OOO execution exists to mitigate data and structural hazards

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[instruction-level-parallelism]]
- [[register-renaming]]
- [[speculation]]
- [[pipeline-hazards]]
- [[miss-shadow]]
