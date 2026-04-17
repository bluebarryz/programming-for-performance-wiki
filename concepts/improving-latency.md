---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[bandwidth-vs-latency]]"
  - "[[profiling]]"
---

# Improving Latency

Although the course mostly focuses on parallelism, improving single-threaded performance is also valuable (and improvements here can help the parallelized version too). Strategies include:

1. **Profile the code** -- Find where time is actually spent. Don't guess.
2. **Do less work** -- Omit unnecessary computation: avoid calculating unneeded intermediate results, compute only to the accuracy required, reduce logging/debugging output (especially in multithreaded contexts where it incurs synchronization cost).
3. **Caching** -- Store results of expensive, side-effect-free operations and reuse them. A hybrid of "do less work" and "be smarter."
4. **Be prepared** -- Pre-generate data the user will likely request (e.g., pre-compute reports and store them).
5. **Be smarter** -- Use a better algorithm (e.g., replace O(n^3) sort with O(n^2)), use smarter data structures, leverage compiler optimizations, be aware of cache and data locality.
6. **Improve the hardware** -- Sometimes the bottleneck is I/O (SSDs, NVMe, more RAM to avoid swapping). Hardware upgrades can be cheaper than developer time. But bad code is still bad on better hardware.

On using assembly: compilers are generally better at generating assembly than humans these days, though giving hints (e.g., vector instructions) can help.

## Prerequisites
- [[bandwidth-vs-latency]] — Understanding the distinction between latency and bandwidth clarifies what "improving latency" targets
- [[profiling]] — Must profile before optimizing to find actual bottlenecks

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[profiling]]
- [[caching]]
- [[bandwidth-vs-latency]]
- [[parallelism]]
