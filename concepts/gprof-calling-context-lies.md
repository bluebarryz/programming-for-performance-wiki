---
tags:
  - concept
  - ece459
  - profiling
lectures:
  - "29"
prerequisites:
  - "[[sampling-vs-instrumentation-profiling]]"
  - "[[cpu-profiling]]"
---

# Gprof Calling Context Lies

Gprof is a profiling tool that combines two data sources: `profil()`, which statistically samples which instruction is executing 100 times per second, and `mcount()`, which exactly records call graph edges via `-pg` instrumentation. The problem is that gprof draws unreliable inferences by combining these statistical and exact data sources.

A classic example: if methods `easy` and `hard` are each called once, but `hard` takes almost all the CPU time, gprof may divide the total time by the number of calls (2) and report that both methods take equal time. This happens because the statistical sampling data lacks calling-context information, and gprof must estimate how to distribute time across callers. Call graph edges are reliable only for functions with a single caller or functions that always take the same time to complete regardless of input.

Results become particularly suspect for functions whose running time depends on their inputs and that are called from multiple contexts. The contribution of children to parents and the total runtime reported as "self+children" can be misleading. This is a concrete example of how profilers can build incorrect narratives from individually correct pieces of evidence, and why understanding your tools' limitations is essential for accurate performance analysis.

## Prerequisites

- [[sampling-vs-instrumentation-profiling]] — gprof combines both sampling and instrumentation, and lies arise from merging the two
- [[cpu-profiling]] — gprof is a CPU profiling tool whose limitations must be understood

## Lectures
- [[L29-Liar-Liar]]

## Related Concepts
- [[profiler-lies]]
- [[sampling-vs-instrumentation-profiling]]
- [[cpu-profiling]]
