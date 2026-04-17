---
tags:
  - concept
  - ece459
  - pogo
  - compiler
  - optimization
lectures:
  - L27
prerequisites:
  - "[[profile-guided-optimization]]"
  - "[[inlining]]"
  - "[[compiler-optimization-levels]]"
---

# POGO Optimizations

During the recompile phase of [[profile-guided-optimization|POGO]], the training data drives nine categories of optimization:

1. **Full and partial inlining** -- the majority of performance gains come from better inlining decisions
2. **Function layout** -- packing related functions together
3. **Speed and size decision** -- hot code is optimized for speed, cold code for size
4. **Basic block layout** -- ordering blocks by execution frequency
5. **Code separation** -- isolating dead/cold code into separate blocks
6. **Virtual call speculation** -- replacing virtual calls with direct calls based on observed types
7. **Switch expansion** -- reordering match/switch cases by likelihood
8. **Data separation** -- grouping frequently accessed data
9. **Loop unrolling** -- informed by actual iteration counts

The inlining decisions are based on [[call-graph-path-profiling]]: the behavior of a function may differ depending on its caller, so the same function might be inlined in one call path but not another.

## Prerequisites

- [[profile-guided-optimization]] — These optimizations are the output of the POGO recompile phase
- [[inlining]] — Most POGO gains come from improved inlining decisions
- [[compiler-optimization-levels]] — POGO optimizations augment standard compiler optimizations

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[profile-guided-optimization]]
- [[hot-and-cold-code]]
- [[call-graph-path-profiling]]
- [[page-locality]]
- [[devirtualization]]
