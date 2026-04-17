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
  - "[[cache-misses]]"
---

# Inlining

Inlining is a compiler optimization that replaces a function call with the body of the called function, inserted directly at the call site. This eliminates function call overhead (pushing/popping the stack frame, jumping) and, more importantly, enables further context-sensitive optimizations that the compiler could not perform across a function boundary.

In Rust, you can control inlining with annotations: `#[inline]` hints the compiler to inline, `#[inline(always)]` requests it unconditionally, and `#[inline(never)]` prevents it. However, inlining is merely a suggestion -- compilers may ignore the hint. In C/C++, taking the address of an inline function or using virtual functions will prevent inlining.

Inlining has a significant downside: increased program size, which can reduce instruction cache hit rates and hurt performance. Some inlines grow very rapidly, so aggressive inlining can paradoxically make programs slower. Debugging is also harder since you cannot set breakpoints in functions that no longer exist as separate entities. For library design, changing an inlined function forces all consumers to recompile -- a non-binary-compatible change. Inlining requires accurate [[call-graphs]] and is closely related to [[devirtualization]], since virtual/dynamic dispatch calls must first be resolved to concrete targets before they can be inlined.

## Examples

### Basic inlining

```rust
#[inline]
fn square(x: i32) -> i32 { x * x }

let y = square(z + 1);
```

After inlining, the compiler sees `let y = (z + 1) * (z + 1)` — no call overhead, and it can now apply [[common-subexpression-elimination]] to avoid computing `z + 1` twice.

### Enabling further optimizations

```rust
fn is_zero(x: i32) -> bool { x == 0 }

if is_zero(count) { return; }
```

Without inlining, the compiler sees an opaque call and must preserve `count`. After inlining, it sees `if count == 0 { return; }` and can fold this into surrounding branch logic, eliminate dead code, or propagate the constant if `count` is known.

### Inlining bloat hurting the instruction cache

```rust
#[inline(always)]
fn validate(record: &Record) -> bool {
    // 200 lines of validation logic
}

for record in records {
    if validate(record) { process(record); }
}
```

Inlining a large function into a hot loop copies 200 lines of code into the loop body. If this pushes surrounding hot code out of the instruction cache, the program gets slower despite eliminating the call overhead. This is why `#[inline(always)]` should be used sparingly.

### Blocking inlining: virtual dispatch

```rust
fn greet(p: &dyn Polite) { p.greet(); }  // cannot inline — target unknown
fn greet(p: &impl Polite) { p.greet(); } // can inline — type known statically
```

`dyn Polite` calls through a vtable; the compiler doesn't know the concrete type at the call site. `impl Polite` (static dispatch) gives the compiler a concrete type, making inlining straightforward. See [[devirtualization]] for how POGO can unlock inlining for the `dyn` case.

## Prerequisites

- [[call-graphs]] — Inlining requires accurate call graphs to know what a callee does
- [[cache-misses]] — Aggressive inlining can hurt instruction cache hit rates

## Lectures

- [[L18-Compiler-Optimizations]]

## Related Concepts

- [[call-graphs]]
- [[devirtualization]]
- [[link-time-optimization]]
- [[tail-recursion-elimination]]
- [[alias-and-pointer-analysis]]
