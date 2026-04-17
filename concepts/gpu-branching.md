---
tags:
  - concept
  - ece459
  - gpu
  - L21
prerequisites:
  - "[[simt]]"
  - "[[gpu-warps]]"
---

# GPU Branching

CUDA implements a [[simt]] architecture with no branch prediction and no speculative execution. This makes branches much more costly than on CPUs.

In practice, the hardware executes all branches that any thread in a [[gpu-warps|warp]] takes, keeping only the results that are valid. For example, an `if/else` in a kernel means both the `if` and `else` bodies execute for all threads in the warp, with unnecessary work discarded. While it won't be possible to avoid all conditional branches, they get expensive quickly.

Similarly, a loop in a warp causes the entire workgroup to wait for the maximum number of iterations any thread needs. The compiler will try to [[gpu-loop-unrolling|unroll loops]] with known iteration counts to mitigate this.

## Prerequisites
- [[simt]] — Branching cost stems from the SIMT execution model
- [[gpu-warps]] — All threads in a warp execute all branches, making divergence costly

## Lectures

- [[L21-GPU-Programming]]

## Related Concepts

- [[simt]]
- [[gpu-warps]]
- [[gpu-loop-unrolling]]
