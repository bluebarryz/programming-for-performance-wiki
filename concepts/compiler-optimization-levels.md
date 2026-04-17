---
tags:
  - concept
  - ece459
  - compiler
  - performance
lectures:
  - L18
prerequisites: []
---

# Compiler Optimization Levels

"Optimization" is a bit of a misnomer -- compilers don't generate optimal code, they generate *better* code. The compiler's contract is to produce a program with the same behaviour as yours, but which runs faster.

In Rust, optimization is controlled via `-O` or `-C opt-level=N`. Most of Rust's optimization happens at the LLVM backend level. The `-C opt-level` option sets inline limits and passes the requested level to LLVM.

## Levels

- **0**: no optimizations, enables `cfg(debug_assertions)`
- **1**: basic optimizations (enables [[constant-propagation]], [[constant-folding]])
- **2**: some optimizations
- **3**: all optimizations
- **"s"**: optimize for binary size
- **"z"**: optimize for binary size, also turns off loop vectorization

For fast release binaries, use `cargo --release` and enable [[link-time-optimization]] in `Cargo.toml`:

```toml
[profile.release]
lto = true
```

Tools like [Godbolt](https://godbolt.org/) are useful for inspecting what the compiler actually emits. Use `-C overflow-checks=n` for cleaner output.

## Prerequisites

None — foundational concept.

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[constant-folding]]
- [[link-time-optimization]]
- [[auto-vectorization]]
- [[inlining]]
