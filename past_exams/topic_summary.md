# Lecture-to-Exam Relevance Summary

How each lecture has appeared across past exams. Relevance levels:
- **Heavy** — 10+ marks directly tested (dedicated question or major sub-question)
- **Moderate** — 3–9 marks (short answer or partial sub-question)
- **Light** — mentioned or tangentially relevant (<3 marks)
- **—** — not tested

| Lecture                                                | W23                                                           | W24                                                              | W25                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------- |
| [[L01-Programming-for-Performance]]                    | **Moderate** — Q1c: Amdahl's speedup calc (3)                 | **Moderate** — Q1a: rate limits (3)                              | **Moderate** — Q1c: Amdahl's + locking (5), Q1i (5)         |
| [[L02-Rust-Basics]]                                    | **Moderate** — Q4a: removing clones (5)                       | **Moderate** — Q1c,d,f: reduced-resource, devops, floats (9)     | **Moderate** — Q1a: clone perf (5)                          |
| [[L03-Rust-Borrowing-Slices-Threads-Traits]]           | **Heavy** — Q1a (3), Q3: buffering (10), Q4a (5), Q4b (5)     | —                                                                | **Moderate** — Q1b: borrowing (5), Q4.4: alias analysis     |
| [[L04-Rust-Breaking-the-Rules]]                        | **Moderate** — Q4b: lifetimes (5)                             | **Light** — Q1b: async I/O (3)                                   | **Light** — Q5: unsafe for Rustacuda                        |
| [[L05-Asynchronous-IO]]                                | **Light** — Q3: buffering context                             | **Moderate** — Q1b: async I/O (3)                                | —                                                           |
| [[L06-Modern-Processors]]                              | **Light** — Q2a: compiler opts context                        | **Moderate** — Q1h: devirtualization (3), Q3.2: POGO (part of 8) | **Moderate** — Q1a (5), Q1g: instruction reorder (5), Q2.5B |
| [[L07-CPU-Hardware-Branch-Prediction]]                 | —                                                             | **Moderate** — Q1g: Stream-VByte SIMD (3)                        | —                                                           |
| [[L08-Cache-Coherency]]                                | —                                                             | —                                                                | —                                                           |
| [[L09-Algorithms-Concurrency-and-Parallelism]]         | **Light** — Q1c: speedup calc                                 | **Moderate** — Q1e: task parallelism (3)                         | **Light** — Q1c                                             |
| [[L10-Software-Architecture]]                          | —                                                             | **Light** — Q4.2: thread context                                 | —                                                           |
| [[L11-Use-of-Locks-Reentrancy]]                        | **Moderate** — Q1a: deadlock (3)                              | —                                                                | **Moderate** — Q1c: fine-grained locking (5)                |
| [[L12-Lock-Convoys-Atomics-Lock-Freedom]]              | —                                                             | —                                                                | **Moderate** — Q2.3: atomic ops for N-Queens (5)            |
| [[L13-Dependencies-and-Speculation]]                   | **Moderate** — Q1d: N-body speculation (3)                    | —                                                                | **Moderate** — Q1d: speculation (5)                         |
| [[L14-Early-Termination-Reduced-Resource-Computation]] | **Moderate** — Q1b: leader election (3)                       | **Heavy** — Q4.1: lifetimes (5), Q4.2: threads+atomics (15)      | **Heavy** — Q1d (5), Q1f (5), Q1i (5), Q2.4 (5)             |
| [[L15-Memory-Consistency]]                             | —                                                             | **Heavy** — Q4.1: lifetimes (5), Q4.2: memory ordering (15)      | **Moderate** — Q2.5B: fences                                |
| [[L16-Rate-Limits]]                                    | —                                                             | —                                                                | —                                                           |
| [[L17-Mostly-Data-Parallelism]]                        | **Heavy** — Q5: Rayon password cracking (10)                  | —                                                                | —                                                           |
| [[L18-Compiler-Optimizations]]                         | **Heavy** — Q1j (3), Q2: compiler vs engineer (20), Q6.2 (15) | —                                                                | **Heavy** — Q4: inlining, const prop, alias analysis (25)   |
| [[L19-Query-Optimization]]                             | —                                                             | **Heavy** — Q6: MESI distributed cache (20)                      | —                                                           |
| [[L20-Self-Optimizing-Software]]                       | **Moderate** — Q6.2: memoization/comemo (15)                  | **Heavy** — Q6: MESI distributed cache (20)                      | **Moderate** — Q2.1: compiled vs interpreted                |
| [[L21-GPU-Programming]]                                | —                                                             | —                                                                | **Heavy** — Q5: GPU programming (25)                        |
| [[L22-GPU-Programming-Continued]]                      | —                                                             | **Heavy** — Q5: CUDA matrix multiply (20)                        | **Heavy** — Q5: Rustacuda (25)                              |
| [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]          | **Moderate** — Q5: password cracking (10)                     | **Heavy** — Q5: CUDA matrix multiply (20)                        | —                                                           |
| [[L24-Profiling-Observing-Operations]]                 | **Moderate** — Q1e: abuse detection (3)                       | —                                                                | **Moderate** — Q2.2: logs/SLAs (5), Q2.5A: RDTSC (5)        |
| [[L25-Load-Testing]]                                   | **Moderate** — Q1f: order-of-magnitude estimation (3)         | —                                                                | —                                                           |
| [[L26-Finding-Bottleneck-Devices]]                     | —                                                             | **Heavy** — Q2: queueing theory M/M/2 (17)                       | —                                                           |
| [[L27-Program-Profiling-and-POGO]]                     | **Heavy** — Q1e (3), Q6.1: flamegraph (5)                     | **Heavy** — Q3: skid + POGO (13)                                 | —                                                           |
| [[L28-Causal-and-Simulation-Profiling]]                | **Moderate** — Q1h: negative speedup (3), Q6.1 (5)            | **Moderate** — Q1i: causal profiling (3)                         | —                                                           |
| [[L29-Liar-Liar]]                                      | —                                                             | —                                                                | **Moderate** — Q1h: super-linear speedup (5)                |
| [[L30-Clusters-Cloud-Computing]]                       | —                                                             | —                                                                | —                                                           |
| [[L31-Introduction-to-Queueing-Theory]]                | **Moderate** — Q1g: time average (3)                          | —                                                                | **Heavy** — Q3: M/M/1 formulas (15)                         |
| [[L32-Convergence-Ergodicity-Applications]]            | **Light** — Q1g: ergodicity                                   | —                                                                | **Heavy** — Q3.4: M/M/k Erlang C (15)                       |
| [[L33-More-Advanced-Queueing-Theory]]                  | —                                                             | —                                                                | **Moderate** — Q3.3: saturation                             |
| [[L34-DevOps-Configuration]]                           | —                                                             | —                                                                | —                                                           |
| [[L35-DevOps-Operations]]                              | —                                                             | **Light** — Q1j: LLMs (3)                                        | —                                                           |

---

## Never-Tested Lectures

These lectures have not appeared on any of the three exams:
- [[L08-Cache-Coherency]] (hardware cache coherency — though MESI was tested via L19/L20 in W24)
- [[L16-Rate-Limits]]
- [[L30-Clusters-Cloud-Computing]]
- [[L34-DevOps-Configuration]]

## Consistently Tested Topics (appeared on all 3 exams)

| Topic | Lectures | W23 | W24 | W25 |
|-------|----------|-----|-----|-----|
| Amdahl's Law / speedup | L01, L09 | Q1c (3) | Q1a,e (6) | Q1c (5) |
| Rust ownership & borrowing | L02, L03 | Q4 (10), Q3 (10) | Q1c,d,f (9) | Q1a,b (10), Q4.4 |
| Reduced-resource computation | L14 | Q1b (3) | Q1c (3) | Q1d,f,i (15), Q2.4 (5) |
| Profiling | L27, L28 | Q1e,h (6), Q6 (20) | Q1i (3), Q3 (13) | Q2.5A (5) |
| Compiler optimizations | L06, L18 | Q1j (3), Q2 (20) | Q1h (3), Q3.2 (8) | Q4 (25) |

## Tested on 2 of 3 Exams

| Topic | Lectures | Exams |
|-------|----------|-------|
| CUDA / GPU | L21, L22, L23 | W24 (20), W25 (25) |
| Queueing theory | L26, L31, L32, L33 | W24 (17), W25 (15) |
| Memory consistency / ordering | L15 | W24 (15), W25 (5) |
| Speculation / N-body | L13 | W23 (3), W25 (5) |
| Deadlock / locking | L11 | W23 (3), W25 (5) |
| Async I/O | L04, L05 | W23 (10), W24 (3) |
| Causal profiling | L28 | W23 (8), W24 (3) |
