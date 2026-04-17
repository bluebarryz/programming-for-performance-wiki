---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L04
prerequisites:
  - "[[borrowing-and-references]]"
  - "[[borrow-checker]]"
---

# Lifetimes

Lifetimes describe how long a reference is valid. The compiler usually infers lifetimes automatically, but sometimes it needs help via explicit lifetime annotations. Annotations are written with an apostrophe followed by a name (e.g., `'a`) and placed on reference parameters and return types to describe the relationships between their lifetimes.

A classic example is a `longest` function that takes two string references and returns one of them. The compiler cannot determine which input the return value borrows from, so you annotate: `fn longest<'a>(x: &'a str, y: &'a str) -> &'a str`. This says the returned reference lives at least as long as the shorter of the two inputs. Annotations do not change how long references live -- they just describe relationships so the compiler can verify safety. In early Rust, lifetime annotations had to be specified everywhere; modern Rust uses *lifetime elision* rules to infer them in common cases.

## Prerequisites
- [[borrowing-and-references]] — Lifetimes describe how long references are valid
- [[borrow-checker]] — The borrow checker uses lifetime information to verify safety

## Lectures
- [[L04-Rust-Breaking-the-Rules]]

## Related Concepts
- [[borrow-checker]]
- [[borrowing-and-references]]
- [[static-lifetime]]
- [[non-lexical-lifetimes]]
