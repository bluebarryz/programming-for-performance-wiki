---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[scalability]]"
  - "[[amdahls-law]]"
  - "[[parallelism]]"
---

# Clusters vs Laptops

The paper "Scalability! But at what COST?" by McSherry, Isard, and Murray (HotOS XV) demonstrates that scaling to big data systems introduces substantial overhead, and a competent single-threaded implementation on a laptop can sometimes match or beat 128-core distributed systems. The key metric they propose is not just scalability but absolute performance: how fast does the system actually solve the problem?

The authors compared a single-threaded laptop implementation against top distributed graph processing systems (Spark, Giraph, GraphLab, GraphX) on PageRank and label propagation tasks using graphs with billions of edges. For PageRank on the twitter_rv dataset, 128-core systems ranged from 249-857 seconds while the laptop took 300 seconds. For label propagation, the distributed systems were even worse at 251-1784 seconds versus 153 seconds on the laptop. Further algorithmic improvements (Hilbert curves for data layout, union-find for connectivity) yielded additional 2-10x speedups on the single machine.

The takeaway for performance engineering is that distributed overhead is real and significant. Before reaching for a cluster, you should verify that it actually outperforms a well-optimized single-machine solution. As the authors put it: "If you are going to build a big data system for others, see that it is faster than my laptop."

## Prerequisites

- [[scalability]] — This concept challenges the assumption that scaling always improves performance
- [[amdahls-law]] — Amdahl's law explains why distributed overhead can negate parallelism gains
- [[parallelism]] — Understanding single-machine parallelism provides the baseline for comparison

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[scalability-cost]]
- [[cloud-computing]]
- [[scalability]]
