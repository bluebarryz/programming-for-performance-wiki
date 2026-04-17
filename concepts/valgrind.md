---
tags:
  - concept
  - ece459
  - profiling
prerequisites:
  - "[[tracing]]"
---

# Valgrind

Valgrind is a memory tracing tool where the target program runs under the tool's "supervision." It checks every memory read and write for validity (is the variable initialized? is the access off the end of an array?), and records information about where memory is allocated to help track down memory leaks. When execution ends, Valgrind shows the stack trace of the path that led to any leaked allocation.

The target program runs dramatically slower than normal under Valgrind. The course notes that it was previously covered more extensively when the course used C and C++, where memory issues were common. With Rust, memory safety is handled by the language itself, making Valgrind's memcheck less relevant. The Helgrind component (for lock acquisition issues) was also dropped because students found too many false positives with Rust code.

## Prerequisites
- [[tracing]] — Valgrind is a memory tracing tool that records every read and write

## Lectures

- [[L24-Profiling-Observing-Operations]]

## Related Concepts

- [[tracing]]
- [[tracing-overhead]]
- [[observability]]
- [[cpu-profiling]]
