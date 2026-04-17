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

# Speculation

Speculation is the processor's ability to execute instructions before it is certain they are needed. The most common form is speculative execution past a branch: when the processor predicts a branch direction, it begins executing instructions along the predicted path before the branch condition is resolved.

If the prediction is correct, the speculative work is committed and execution proceeds without delay. If incorrect, the speculative results are discarded and the pipeline is flushed.

Speculation works together with [[register-renaming]] to keep speculative state separate from committed state. It allows the processor to get past a [[cache-misses|cache miss]] and start working on the next miss sooner, which is critical for performance since cache misses dominate execution time.

Speculation is also the mechanism exploited by [[spectre-and-meltdown]] attacks, where speculatively executed code can leak data through the cache.

## Prerequisites

- [[pipelining]] — Speculation keeps the pipeline full by executing instructions before knowing if they are needed
- [[pipeline-hazards]] — Speculation addresses control hazards caused by branches

## Lectures

- [[L06-Modern-Processors]]

## Related Concepts

- [[branch-prediction]]
- [[register-renaming]]
- [[out-of-order-execution]]
- [[spectre-and-meltdown]]
- [[pipeline-hazards]]
