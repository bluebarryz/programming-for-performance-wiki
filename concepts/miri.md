---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "28"
prerequisites:
  - "[[flamegraph]]"
  - "[[simulation-profiling]]"
---

# Miri

Miri is an interpreter for Rust's Mid-level Intermediate Representation (MIR) that can be used for both bug detection and profiling. It runs Rust code in an interpreted environment, which makes execution much slower but enables detailed analysis. Miri shares many similarities with Valgrind, catching issues like array bounds violations, reading uninitialized memory, and memory leaks, with a particular focus on detecting problems in unsafe code.

Beyond bug detection, Miri can generate flamegraph-style profiling results. By running with flags like `-Zmiri-disable-isolation -Zmiri-measureme=crox`, it produces trace data that can be processed with the crox tool into a JSON file viewable in Chrome DevTools. This provides call hierarchy and timing information similar to a traditional flamegraph.

A caveat is that Miri interprets the unoptimized debug version of the code, so optimizations suggested by Miri profiling may not translate to improvements in the release build. The compiler's own optimizations in the release version may already handle many of the inefficiencies visible under Miri. Still, Miri provides a useful signal for the change-run-evaluate optimization loop, particularly for understanding relative costs of different code paths.

## Prerequisites

- [[flamegraph]] — Miri produces flamegraph-style profiling output
- [[simulation-profiling]] — Miri is a simulation-based profiler that interprets code rather than running it natively

## Lectures
- [[L28-Causal-and-Simulation-Profiling]]

## Related Concepts
- [[simulation-profiling]]
- [[flamegraph]]
- [[profiling]]
