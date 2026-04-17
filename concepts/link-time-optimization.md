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

## Examples

### Cross-module inlining

Without LTO, the compiler sees each file in isolation. `math.rs` and `main.rs` compile separately, so `square` cannot be inlined into `main`:

```rust
// math.rs
pub fn square(x: i32) -> i32 { x * x }

// main.rs
fn main() {
    let y = math::square(4);  // function call — cannot inline across modules without LTO
}
```

With LTO, the whole-program analysis phase sees both modules together and inlines `square` directly, eliminating the call overhead.

### Interprocedural constant propagation

Without LTO, the compiler cannot tell whether `helper()` modifies `VALUE`, so it must reload it after the call:

```rust
// config.rs
pub static VALUE: i32 = 42;

// helper.rs
pub fn helper() { /* does not touch VALUE */ }

// main.rs
fn main() {
    println!("{}", config::VALUE);  // load VALUE
    helper::helper();
    println!("{}", config::VALUE);  // must reload — compiler can't see helper's body
}
```

With LTO, the whole-program analysis confirms `helper` never writes to `VALUE`, so the second load is eliminated and the constant `42` can be propagated directly.

### Dead function elimination

A function exported from a library but never called anywhere in the final binary gets eliminated:

```rust
// utils.rs
pub fn unused_export() -> i32 { expensive_computation() }  // removed by LTO
pub fn used_export() -> i32 { 1 }
```

Without LTO, `unused_export` must be kept because the linker doesn't know if another module calls it. With LTO, the whole-program call graph makes it visible that no call site exists.

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
