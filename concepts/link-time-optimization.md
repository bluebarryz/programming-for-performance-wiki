---
tags:
  - concept
  - ece459
  - compiler
  - optimization
lectures:
  - L18
prerequisites:
  - "[[call-graphs]]"
  - "[[inlining]]"
  - "[[compiler-optimization-levels]]"
---

# Link-Time Optimization

Link-time optimization (LTO) performs interprocedural optimizations across the entire program at link time, when all compilation units are available together. In Rust, LTO is enabled by adding `lto = true` to the `[profile.release]` section of `Cargo.toml`. The process works in three phases: local generation (parallelizable) compiles each module to intermediate representation; whole-program analysis (hard to parallelize) builds the [[call-graphs|call graph]] and makes transformation decisions; and local transformations (parallelizable) carry out the optimizations and generate final object code.

LTO enables transformations that are impossible when compiling modules independently: cross-module [[inlining]], virtual function inlining, interprocedural constant propagation, dead function/variable elimination, and field reordering or struct reorganization. The biggest challenge is scalability -- large codebases like Firefox or Chromium contain tens of millions of lines of code. Loading the entire IR into memory is prohibitive, so compilers use techniques like call graph partitioning (grouping related functions together) and approximating functions in other partitions.

The evolution of LTO in gcc illustrates classic performance optimization: gcc 4.5 had the initial version; 4.6 added parallelization and call graph partitioning; 4.7-4.9 improved build times and memory usage by "chasing unnecessary data away." In practice, LTO yields 3-5% performance improvements, which compiler experts consider good. LLVM LTO can optimize across source languages -- if a program contains both C and Rust, the linker can optimize both using the shared intermediate representation.

## Prerequisites

- [[call-graphs]] — LTO builds whole-program call graphs to enable cross-module optimizations
- [[inlining]] — Cross-module inlining is one of the key optimizations LTO enables
- [[compiler-optimization-levels]] — LTO is enabled alongside optimization levels in the build configuration

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[call-graphs]]
- [[inlining]]
- [[alias-and-pointer-analysis]]
- [[devirtualization]]
- [[compiler-optimization-levels]]
