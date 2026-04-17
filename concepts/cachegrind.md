---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "28"
prerequisites:
  - "[[cache-misses]]"
  - "[[branch-prediction]]"
  - "[[memory-hierarchy]]"
---

# Cachegrind

Cachegrind is a tool in the Valgrind suite that simulates how a program interacts with the CPU cache hierarchy and evaluates branch prediction performance. Unlike memcheck or Helgrind which focus on correctness, Cachegrind is directly performance-oriented. It reports data on the First Level Instruction Cache (I1), the First Level Data Cache (D1), and the Last Level Cache (LL, typically L3).

The tool works by simulation rather than measuring the actual hardware, which means it can provide detailed, deterministic results about cache miss rates and branch misprediction rates. A miss from the fastest cache costs roughly 10 cycles, a miss requiring a trip to main memory costs about 200 cycles, and a mispredicted branch costs 10-30 cycles. When profiling with Cachegrind, you should compile with optimizations enabled (release mode) but with debug symbols, since you want results that reflect the optimized binary's behavior.

Cachegrind produces a detailed output file (cachegrind.out.<pid>) that can be processed with cg_annotate to get line-by-line cache and branch prediction statistics alongside source code. The tool is invoked with `valgrind --tool=cachegrind --branch-sim=yes`. While very verbose, Cachegrind is well-suited for quantifying whether a specific code change improved cache behavior and understanding the mechanism behind performance differences.

## Prerequisites

- [[cache-misses]] — Cachegrind simulates and counts cache misses at each level of the hierarchy
- [[branch-prediction]] — Cachegrind also simulates branch prediction performance
- [[memory-hierarchy]] — Understanding the cache hierarchy is essential to interpreting Cachegrind output

## Lectures
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts
- [[cache-misses]]
- [[branch-prediction]]
- [[simulation-profiling]]
- [[profiling]]
