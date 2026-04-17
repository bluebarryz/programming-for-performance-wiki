---
tags:
  - concept
  - ece459
  - hardware
  - L06
prerequisites: []
---

# Von Neumann Architecture

The classic von Neumann machine architecture stores both instructions and data in the same memory, and executes a program sequentially -- one statement at a time, one after another. As the course notes, this is not really how modern computers work, but it remains a useful abstraction for algorithm analysis.

The key limitation is that sequential execution leaves performance on the table. Modern processors use techniques like [[pipelining]], [[out-of-order-execution]], and [[speculation]] to break away from strict sequential execution while maintaining the illusion of it.

## Prerequisites

None — foundational concept.

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[pipelining]]
- [[instruction-level-parallelism]]
- [[cisc-vs-risc]]
