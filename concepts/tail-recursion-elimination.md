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
---

# Tail Recursion Elimination

Tail recursion elimination is a compiler optimization that replaces a recursive function call in tail position (the last operation before returning) with a jump back to the beginning of the function, effectively converting recursion into iteration. This avoids function call overhead and, critically, **prevents call stack growth,** which would otherwise lead to stack overflow for deep recursions.

A function call is in "tail position" when there is no further work to do after the recursive call returns. For example, in a Fibonacci implementation using an accumulator pattern, the recursive call `fibonacci_lr(n - 1, a + b, a)` __is the last thing the function does__, so the current stack frame can be reused. This optimization is mandatory in some functional languages (like Scheme) but is not guaranteed in C, C++, or Rust. In Rust, LLVM may or may not perform the transformation depending on optimization level and the specific code pattern.

The practical benefit is turning an O(n) stack space algorithm into O(1) stack space while preserving the recursive coding style. This is one of the interprocedural optimizations that benefits from [[call-graphs]] and is related to [[inlining]] in that both transform function call boundaries to reduce overhead.

## Examples
### Fibonacci

**Unoptimized** — not in tail position; the `+` operation happens after the recursive call returns, so the stack frame cannot be reused:

```rust
fn fibonacci(n: u64) -> u64 {
    if n <= 1 { return n; }
    fibonacci(n - 1) + fibonacci(n - 2)  // addition happens after return
}
```

**Optimized** — accumulator pattern puts the recursive call in tail position; LLVM can replace the call with a jump, reusing the stack frame:

```rust
fn fibonacci(n: u64, a: u64, b: u64) -> u64 {
    if n == 0 { return a; }
    fibonacci(n - 1, b, a + b)  // last operation — no work after this
}
```

The unoptimized version grows the call stack O(n) deep. The optimized version runs in O(1) stack space.

### Factorial

**Factorial — unoptimized:**

```rust
fn factorial(n: u64) -> u64 {
    if n == 0 { return 1; }
    n * factorial(n - 1)  // multiplication happens after return
}
```

**Factorial — optimized:**

```rust
fn factorial(n: u64, acc: u64) -> u64 {
    if n == 0 { return acc; }
    factorial(n - 1, acc * n)  // last operation — accumulator carries the result
}
```

## Prerequisites

- [[call-graphs]] — Tail recursion elimination is an interprocedural optimization that transforms function call boundaries
- [[inlining]] — Related optimization that also reduces function call overhead

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[inlining]]
- [[call-graphs]]
- [[compiler-optimization-levels]]
- [[link-time-optimization]]
