---
tags:
  - concept
  - ece459
  - gpu
  - L22
prerequisites:
  - "[[cuda-host-code]]"
---

# CUDA Context

A CUDA context is analogous to a process. When you launch something within a context, it executes there with its own address space, and when the context is destroyed, all its resources are cleaned up.

Each host thread may have one context. The context is created with "create and push" because each host thread has a stack of current contexts. In simple programs where everything happens in `main`, the context stays in scope naturally. In more structured programs, you must ensure the context does not go out of scope before other CUDA operations complete.

## Prerequisites
- [[cuda-host-code]] — Context creation is an early step in the host code launch sequence

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-host-code]]
- [[rustacuda]]
