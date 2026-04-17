---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[borrow-checker]]"
  - "[[ownership]]"
---

# Unsafe Rust

Unsafe Rust is an escape hatch that lets you perform operations the compiler cannot verify as safe. You declare an `unsafe` block, and inside it you can: call unsafe functions, access or modify [[mutable-static-variables]], implement unsafe traits, access fields of [[unions]], and dereference [[raw-pointers]]. The [[borrow-checker]] still runs inside unsafe blocks -- `unsafe` does not grant unlimited power.

Unsafe blocks should be small so that if something goes wrong, the bug is easy to find. Unsafe functions impose additional restrictions on their callers, who must ensure the documented safety conditions are met. If an unsafe block is not inside an unsafe function, you are promising that the function is unconditionally safe to call, encapsulating the unsafety. Getting unsafe code wrong brings back all the problems Rust prevents: race conditions, segmentation faults, and memory leaks.

## Prerequisites
- [[borrow-checker]] — Unsafe is an escape hatch from the borrow checker's restrictions
- [[ownership]] — Unsafe relaxes ownership guarantees that the compiler normally enforces

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[raw-pointers]]
- [[mutable-static-variables]]
- [[unions]]
- [[borrow-checker]]
