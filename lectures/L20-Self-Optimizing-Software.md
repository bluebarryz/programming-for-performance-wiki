---
tags:
  - lecture
  - ece459
  - performance
  - runtime-optimization
  - jit
lecture: 20
title: Self-Optimizing Software
prerequisite_lectures:
  - "[[L18-Compiler-Optimizations]]"
---

# L20 - Self-Optimizing Software

This lecture moves beyond compile-time optimizations to explore how software can optimize itself at runtime. It starts with simple approaches (caching, observe-and-change configuration) and progresses to more advanced techniques: genetic algorithms for tuning configuration parameters, JIT compilation (Hotspot JVM) with escape analysis, lock elision/coarsening, on-stack replacement, and intrinsics. It concludes with binary rewriting -- having the program recompile segments of itself at runtime using an available compiler -- and the practical concern that self-modifying binaries may trigger anti-virus heuristics.

## Prerequisite Lectures
- [[L18-Compiler-Optimizations]] — Compile-time optimizations needed to understand what runtime/JIT optimization builds upon

## Concepts Covered

- [[observe-and-change]]
- [[genetic-algorithms]]
- [[jit-compilation]]
- [[escape-analysis]]
- [[lock-elision-and-coarsening]]
- [[on-stack-replacement]]
- [[intrinsics]]
- [[binary-rewriting]]
