---
tags:
  - concept
  - ece459
  - runtime-optimization
lectures:
  - L20
prerequisites:
  - "[[jit-compilation]]"
---

# On-Stack Replacement

On-stack replacement (OSR) is a technique used by virtual machines (primarily the JVM) to switch between implementations of a method while it is executing. When the JIT compiler identifies a function as "hot" (frequently called), it can compile a more optimized version and swap it in, replacing the currently-executing stack frame with one organized for the new implementation.

OSR has a slight cost: the virtual machine must pause execution briefly to perform the swap, potentially recompile the method (though this can happen on a separate thread), and definitely rearrange the stack frame since the new version may organize local variables differently. Despite this cost, OSR provides a net benefit for frequently-executed code because the improved version will be used for all subsequent calls and iterations.

This mechanism is also visible during JVM debugging: with a debugger attached, you can edit source code, recompile, and the JVM will attempt to swap in the new code for the old code via OSR without stopping the program. This does not always succeed, but when it does, it allows testing changes without restarting -- particularly helpful when the application has a long startup time or when reproducing a bug requires a lengthy workflow.

## Prerequisites

- [[jit-compilation]] — OSR is a JIT technique for swapping in optimized code while a method executes

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[jit-compilation]]
- [[escape-analysis]]
- [[intrinsics]]
- [[binary-rewriting]]
