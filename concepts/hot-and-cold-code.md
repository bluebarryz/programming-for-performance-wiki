---
tags:
  - concept
  - ece459
  - pogo
  - optimization
lectures:
  - L27
prerequisites:
  - "[[profile-guided-optimization]]"
  - "[[cache-misses]]"
---

# Hot and Cold Code

In [[profile-guided-optimization|POGO]], code is classified as **hot** (performance-critical, frequently executed) or **cold** (rarely executed). The compiler applies different strategies to each:

- **Hot code**: optimized for speed, even at the cost of larger binary size (e.g., aggressive inlining)
- **Cold code**: optimized for minimal binary size to avoid polluting the instruction cache

It is recommended that less than 5% of methods should be compiled for speed. "Dead" code (code never executed in any training run) is placed in its own special block, separate from both hot and cold code.

## Prerequisites

- [[profile-guided-optimization]] — Hot/cold classification comes from POGO training data
- [[cache-misses]] — The hot/cold split exists to minimize instruction cache misses

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[profile-guided-optimization]]
- [[pogo-optimizations]]
- [[page-locality]]
