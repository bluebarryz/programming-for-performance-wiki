---
tags:
  - lecture
  - ece459
  - profiling
  - simulation
  - causal-profiling
lecture: 28
title: Causal and Simulation Profiling
date: 2025-07-08
prerequisite_lectures:
  - "[[L27-Program-Profiling-and-POGO]]"
---

# L28 - Causal and Simulation Profiling

This lecture introduces causal profiling (Coz) as a way to predict the impact of optimizing a particular piece of code without actually changing it. The key insight is that speeding up one section is equivalent to slowing down everything else (virtual speedup). The lecture also covers SCOZ, a system-wide extension of Coz that operates at the core level. The second half discusses simulation-based profiling tools: Cachegrind (cache and branch-prediction simulation from the Valgrind suite), simulation as performance debugging, and Miri (a Rust interpreter that can produce flamegraph-style profiling output).

## Prerequisite Lectures
- [[L27-Program-Profiling-and-POGO]] — Need profiling methods (sampling vs instrumentation) before causal and simulation profiling

## Concepts Covered

- [[causal-profiling]]
- [[virtual-speedup]]
- [[coz-profiler]]
- [[scoz]]
- [[cachegrind]]
- [[simulation-profiling]]
- [[miri]]
