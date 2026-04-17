---
tags:
  - concept
  - ECE459
  - L01
  - performance
prerequisites:
  - "[[profiling]]"
  - "[[scalability]]"
---

# Laws of Performant Software

Crista Videira Lopes' Five Laws of Performant Software:

1. **Programming language << Programmers' awareness of performance.** No programming language is magic. All major languages allow you to write programs that perform well or badly. Some languages lend themselves better to parallelization, but the way of thinking can be applied across languages.

2. **Small details matter** (the butterfly effect / chaos theory). A small code change can have a huge performance impact. Don't overlook the small stuff -- a single `free()` call, proper caching, a faster serialization algorithm.

3. **corr(performance degradation, unbounded resource usage) > 0.9.** There is a very high correlation between performance degradation and unbounded use of resources. Resources need to be limited: thread pools should have fixed sizes, caches need maximum sizes, request queues need bounds.

4. **Performance improvements = log(controlled experiments).** If you want your code to be faster, you have to know why it is slow. Don't guess; measure.

5. **N * bad != good.** No amount of nodes, cores, memory, etc. will save you from poorly-written code. Bad code is still bad no matter how much hardware you throw at it.

## Prerequisites
- [[profiling]] — Law 4 is built on the principle of measuring before optimizing
- [[scalability]] — Law 3 connects unbounded resource usage to performance degradation at scale

## Lectures

- [[L01-Programming-for-Performance]]

## Related Concepts

- [[profiling]]
- [[scalability]]
- [[improving-latency]]
