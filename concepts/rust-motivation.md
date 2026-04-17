---
tags:
  - concept
  - ECE459
  - L01
  - L02
  - rust
prerequisites:
  - "[[data-races]]"
  - "[[parallelism]]"
---

# Rust Motivation

Previous courses in ECE used C and C++ as systems languages, but these make it hard (or impossible) to write code that is simultaneously fast, correct, and secure. Robert O'Callahan (PhD from CMU, Distinguished Engineer at Mozilla): "I cannot consistently write safe C/C++ code." Even Google, with best practices and top developers, disclosed Chrome use-after-free 0-days in 2019.

The advice to "try harder" doesn't work. What we want is to make mistakes difficult-to-impossible, or mitigate their effects. Tools like Valgrind and Coverity help but are incomplete. Static analysis at compile time is a better approach -- solving entire classes of problems rather than individual instances.

Rust is an alternative to C/C++, incorporating good ideas from C++ (RAII, references) and sometimes improving on them. A design goal of Rust is to avoid issues with memory allocation and concurrency by checking things at compile time. Rust is from Mozilla's Project Quantum.

Rust is not always faster than C++ (e.g., exceptions vs `Result` types). Trade-offs sometimes make things harder to code in Rust than C/C++, but the code is more likely to be correct.

## Prerequisites
- [[data-races]] — Rust is motivated by preventing data races that plague C/C++
- [[parallelism]] — Rust aims to make safe parallel programming practical

## Lectures

- [[L01-Programming-for-Performance]]
- [[L02-Rust-Basics]]

## Related Concepts

- [[ownership]]
- [[fearless-concurrency]]
- [[raii]]
- [[garbage-collection-vs-ownership]]
