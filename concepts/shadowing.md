---
tags:
  - concept
  - ECE459
  - L02
  - rust
prerequisites:
  - "[[immutability-by-default]]"
---

# Shadowing

Shadowing lets you reuse a variable name by re-declaring it with `let`. This is not the same as mutation -- it creates a new variable that happens to have the same name. The old variable can no longer be used.

A common use case: parsing a string into a number. Instead of naming them `guess_string` and `guess_int`, you can shadow:

```rust
let guess = String::new();
// ... read input into guess ...
let guess: u32 = guess.trim().parse().expect("Please type a number!");
```

Conceptually there are two variables (one `String`, one `u32`) that share the same name. Rust promises that the shadowed variable has no remaining aliases.

## Prerequisites
- [[immutability-by-default]] — Shadowing is an alternative to mutation for reusing variable names

## Lectures

- [[L02-Rust-Basics]]

## Related Concepts

- [[immutability-by-default]]
- [[ownership]]
