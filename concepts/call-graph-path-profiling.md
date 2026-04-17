---
tags:
  - concept
  - ece459
  - pogo
  - profiling
lectures:
  - L27
prerequisites:
  - "[[profile-guided-optimization]]"
  - "[[call-graphs]]"
  - "[[inlining]]"
---

# Call Graph Path Profiling

Call graph path profiling records not just how often a function is called, but **from where** it is called and how often each call path is taken. This is critical for [[profile-guided-optimization|POGO]] because a function's behavior may differ dramatically depending on its caller.

For example, if `bar` is called 100 times from `bat` but only 10 times from `goo`, it makes sense to inline `bar` into `bat` (for speed) but not into `goo` (to avoid code size bloat with minimal performance benefit). Each part of the call path is considered separately when making inlining decisions.

The majority of POGO's performance gains come from these context-sensitive inlining decisions driven by call graph path profiling data.

## Prerequisites

- [[profile-guided-optimization]] — Call graph path profiling provides the data that drives POGO inlining decisions
- [[call-graphs]] — Understanding call graphs is necessary to reason about call paths
- [[inlining]] — The primary use of call graph path data is making context-sensitive inlining decisions

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[profile-guided-optimization]]
- [[pogo-optimizations]]
- [[hot-and-cold-code]]
