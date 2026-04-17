---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[unsafe-rust]]"
---

# Unions

A `union` in Rust is similar to a C union: like a `struct`, but it stores only one of its fields at a time (e.g., an integer *or* a floating point number *or* a pointer, not all three). There is no way to know at runtime which field is currently stored, so accessing the fields of a union requires an `unsafe` block. "Type punning" -- reinterpreting the bits of one type as another -- is what you can do when accessing union fields.

Unions exist in Rust primarily for FFI (foreign function interface) compatibility with C APIs that use unions. Most Rust code should use enums (tagged unions / discriminated unions) instead, which track which variant is active and can be matched safely.

## Prerequisites
- [[unsafe-rust]] — Accessing union fields requires an unsafe block

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[unsafe-rust]]
- [[raw-pointers]]
