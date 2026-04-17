---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "28"
prerequisites:
  - "[[cpu-profiling]]"
  - "[[cache-misses]]"
---

# Simulation Profiling

Simulation profiling uses a simulated execution environment to analyze program performance, as opposed to measuring the actual hardware during execution. This approach trades speed for precision and the ability to observe details that are invisible in hardware-based profiling.

[[Cachegrind]] is a key example: it simulates the CPU cache hierarchy and branch predictor to count exact cache misses, hits, and branch mispredictions for each line of code. This provides deterministic, reproducible results unaffected by other system activity. Beyond counting events, simulation enables performance debugging: halting on event triggers like pipeline stalls to understand how the program reached that state, not just that it happened. The TMS320C55x instruction set simulator from Texas Instruments demonstrates this capability for embedded systems.

[[Miri]], the Rust MIR interpreter, takes a different simulation approach by interpreting Rust code directly rather than compiling and running it. This enables detailed profiling with flamegraph-style output, though it operates on unoptimized code. The general tradeoff of simulation profiling is much slower execution (Valgrind and Miri both impose large slowdowns) in exchange for more precise, deterministic, and detailed performance data than hardware-based measurement can provide.

## Prerequisites

- [[cpu-profiling]] — Simulation profiling is an alternative to hardware-based CPU profiling
- [[cache-misses]] — Simulation tools like Cachegrind focus on cache behavior

## Lectures
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts
- [[cachegrind]]
- [[miri]]
- [[profiling]]
- [[cache-misses]]
