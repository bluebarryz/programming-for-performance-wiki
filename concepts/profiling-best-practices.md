---
tags:
  - concept
  - ece459
  - profiling
  - methodology
lectures:
  - L27
prerequisites:
  - "[[bottleneck-analysis]]"
  - "[[cpu-profiling]]"
---

# Profiling Best Practices

Guidelines for effective profiling:

- **Start early**: profile and benchmark as soon as the system can run, to establish a baseline performance and track regressions
- **Write correct code first**: don't do premature optimizations, but do make reasonable choices (e.g., efficient algorithms) when they cost nothing extra
- **Focus on what matters**: optimize the code that actually consumes the most time

Look for abnormalities -- specifically, deviations from these rules:
- Time is spent in the right part of the system/program
- Time is NOT spent in error-handling, noncritical code, or exceptional cases
- Time is NOT unnecessarily spent in the operating system

**Development vs production**: you can always profile in development, but production systems have different characteristics. Tools like DTrace can profile production systems without affecting performance or reliability.

## Prerequisites

- [[bottleneck-analysis]] — Best practices assume you know how to identify which resource to profile
- [[cpu-profiling]] — These guidelines apply primarily to CPU profiling workflows

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[cpu-profiling]]
- [[perf-tool]]
- [[sampling-vs-instrumentation-profiling]]
