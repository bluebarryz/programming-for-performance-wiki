---
tags:
  - concept
  - ece459
  - gpu
  - L14
  - L21
  - L22
prerequisites:
  - "[[cuda-kernel]]"
  - "[[cuda-blocks-and-grids]]"
  - "[[data-parallelism]]"
---

# N-Body Problem

The N-body problem simulates the movement of N bodies that interact via gravitational forces. Each body's motion depends on the force exerted by every other body, following F = Gm₁m₂/r². It appears across three lectures in ECE 459 as a recurring example: first as a candidate for accuracy-vs-time tradeoffs (L14), then as a GPU kernel (L21), and finally as a full CUDA launch with grid tuning (L22).

## L14 — Reduced-Resource Computation

In [[L14-Early-Termination-Reduced-Resource-Computation]], the N-body problem is introduced as a physics simulation well suited to parallelization: forces on each body can be computed from all other bodies in parallel. It was once an OpenCL assignment in the course, replaced because too many solutions exist online.

The lecture uses N-body to demonstrate **reduced-resource computation via domain knowledge**. Since force falls off with 1/r², faraway bodies contribute negligibly and can be approximated:

- **Bin-based approximation:** divide space (e.g., [0, 1000]³) into cubic bins (e.g., 100³ bins of side 10), compute a center of mass per bin, and when calculating forces on a point:
  - Use exact pairwise calculation for points in the same bin and the 26 directly-adjacent bins (Rubik's Cube neighbourhood — 27 bins total).
  - Use the bin's center of mass as a single proxy body for bins farther away.
- **Tuning knob:** more bins → higher accuracy; fewer/larger bins → more speed.
- **Overhead trade-off:** must (1) assign each point to a bin, (2) compute per-bin center of mass, (3) branch on near vs. far when computing forces.

Benchmarks with 100,000 points (no threads):
- Unmodified: ~162s
- Bin-approximated: ~147s
- Rayon-parallelized (either version): ~25s

Key lesson: parallelization dominated the accuracy-for-time tradeoff in this implementation, but on sufficiently large problems every optimization counts. An even cruder approximation — using `float` instead of `double` — is mentioned as the first thing to try.

## L21 — GPU Programming (CUDA)

In [[L21-GPU-Programming]], N-body is the motivating example for data parallelism on GPUs. Each body is a work-item; the natural index space is 1-D over the N bodies.

The lecture presents the full CUDA kernel (brute-force, no approximations):

```c
__device__ void body_body_interaction(float4 point1, float4 point2, float3 *acceleration) { ... }

extern "C" __global__ void calculate_forces(const float4* positions, float3* accelerations, int num_points) {
    if (blockIdx.x >= num_points) return;
    float4 current = positions[blockIdx.x];
    float3 acc = accelerations[blockIdx.x];
    for (int i = 0; i < num_points; i++) {
        body_body_interaction(current, positions[i], &acc);
    }
    accelerations[blockIdx.x] = acc;
}
```

N-body illustrates several CUDA concepts:
- **Vector types:** `float4` packs (x, y, z, mass) for a body, `float3` packs the acceleration — no need for custom structs.
- **`__device__` vs. `__global__`:** `body_body_interaction` is `__device__` (GPU-internal helper); `calculate_forces` is `__global__` (entry point callable from host). Global functions cannot call other global functions.
- **`extern "C"`:** disables name mangling so the host can find the kernel by name.
- **Dimensionality choice:** N-body is used as a counter-example for 2-D index spaces. Treating each (i, j) pair as a work-item sounds like more parallelism, but the per-pair work is too tiny to justify the overhead — a 1-D index over bodies is the right choice here. For kernels with heavier per-pair work, 2-D could pay off.

## L22 — GPU Programming Continued

In [[L22-GPU-Programming-Continued]], N-body returns as the full host-side example, showing how Rustacuda drives the kernel from L21. It is also the case study for **why grid/block sizing matters**.

Host-side highlights:
- Wraps `float4`/`float3` from `cuda-sys` in newtypes `CudaFloat4`/`CudaFloat3` to implement the `DeviceCopy` trait (promises no host pointers inside — required by Rustacuda).
- Standard launch flow: init → get device → push context → load PTX module → create stream → upload `DeviceBuffer`s → `launch!` → `stream.synchronize()` → copy results back.

Benchmarks on ecetesla1 with 100,000 points:

| Version | Time |
| --- | --- |
| Sequential CPU | 40.3s |
| Parallel CPU (Rayon) | 5.3s |
| CUDA, 1 thread per block (`NUM_POINTS` blocks × 1 thread) | 9.5s |
| CUDA, 256 threads per block (`NUM_POINTS/256 + 1` blocks × 256 threads) | 1.65s |

The naive CUDA version was **slower than the parallel CPU**. Profiling showed the time was spent inside `calculate_forces`; the root cause was underuse of the warp hardware — one thread per block wastes 31 of every 32 warp lanes.

Fixing it required two changes:
1. Launch with `<<<(NUM_POINTS/256) + 1, 256, 0, stream>>>` (the `+1` handles non-divisibility, otherwise trailing accelerations stay zero).
2. Change the kernel's index from `blockIdx.x` alone to `threadIdx.x + blockIdx.x * blockDim.x`, since 256 work-items now share a block.

Guidance from the lecture: threads per block should be a multiple of 32 (warp size), capped at 512–1024 depending on hardware; 128 or 256 are good starting points.

**Bonus accuracy-for-performance angle (also L22):** consumer NVIDIA GPUs emulate FP64 in software at 1/16 to 1/64 the speed of FP32, so using `float4`/`float3` instead of doubles is itself a massive reduced-resource optimization for N-body on gaming GPUs.

## Prerequisites
- [[cuda-kernel]] — The N-body simulation is implemented as a CUDA kernel
- [[cuda-blocks-and-grids]] — Performance depends critically on proper block and grid sizing
- [[data-parallelism]] — The N-body problem is a data-parallel workload where each body is a work-item

## Lectures

- [[L14-Early-Termination-Reduced-Resource-Computation]]
- [[L21-GPU-Programming]]
- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-kernel]]
- [[cuda-blocks-and-grids]]
- [[cuda-grid-sizing]]
- [[cuda-host-code]]
- [[reduced-resource-computation]]
