---
tags:
  - concept
  - ece459
  - L13
  - parallelism
  - dependencies
prerequisites:
  - "[[dependencies-in-parallelism]]"
  - "[[parallelism]]"
---

# Loop-Carried Dependencies

A loop-carried dependency exists when executing an iteration of a loop depends on the result of a previous iteration. This prevents parallelizing loop iterations.

Example:
```rust
for i in 1..vec.len() {
    vec[i] = vec[i-1] + 1;
}
```
Each iteration reads the value written by the previous iteration, so no out-of-order execution is safe.

However, if the dependency has a stride greater than 1, partial parallelization is possible. For example, with stride 4 (`vec[i] = vec[i-4] + 1`), four independent chains exist and can execute in parallel.

The Mandelbrot set is a real-world example: each point's iteration depends on the previous (x, y) values, so a single point must be computed sequentially. But different points are independent, making it an embarrassingly parallel problem at the outer level.

## Prerequisites

- [[dependencies-in-parallelism]] — Understanding that dependencies block parallel execution
- [[parallelism]] — Understanding why we want to parallelize loop iterations

## Lectures

- [[L13-Dependencies-and-Speculation]]

## Related Concepts

- [[dependencies]]
- [[memory-carried-dependencies]]
- [[critical-path]]
