# Question-by-Question Concept Mapping

## Q1: Short Answer (30 marks)

* **Sub: (a)**
    * **Topic:** `.clone()` performance
    * **Lectures:** [[L02-Rust-Basics]], [[L06-Modern-Processors]]
    * **Key Concepts:** [[ownership]], [[move-semantics]], [[cache-misses]], [[memory-hierarchy]]
    * **Solution Insight:** More memory allocated = worse data cache performance/locality

* **Sub: (b)**
    * **Topic:** Alternative to clone
    * **Lectures:** [[L03-Rust-Borrowing-Slices-Threads-Traits]]
    * **Key Concepts:** [[borrowing-and-references]]
    * **Solution Insight:** Just borrowing — `fn calculate_length(s: &String)`

* **Sub: (c)**
    * **Topic:** Amdahl's + fine-grained locking
    * **Lectures:** [[L01-Programming-for-Performance]], [[L09-Algorithms-Concurrency-and-Parallelism]], [[L11-Use-of-Locks-Reentrancy]]
    * **Key Concepts:** [[amdahls-law]], [[fine-grained-locking]], [[locking-granularity]]
    * **Solution Insight:** Must calculate actual speedup numbers ($S=10, P=10$ example)

* **Sub: (d)**
    * **Topic:** Speculation in N-body
    * **Lectures:** [[L13-Dependencies-and-Speculation]], [[L14-Early-Termination-Reduced-Resource-Computation]]
    * **Key Concepts:** [[speculative-execution]], [[value-speculation]], [[n-body-problem]], [[reduced-resource-computation]]
    * **Solution Insight:** Yes it helps — assume far, subtract close ones. Was recommended in assignment

* **Sub: (e)**
    * **Topic:** Bounds check elimination
    * **Lectures:** [[L18-Compiler-Optimizations]], [[L03-Rust-Borrowing-Slices-Threads-Traits]]
    * **Key Concepts:** [[iterator-trait]], [[compiler-optimization-levels]]
    * **Solution Insight:** Iterators in idiomatic Rust don't need bounds checks — no out-of-bounds access generated

* **Sub: (f)**
    * **Topic:** Reduced-resource computation
    * **Lectures:** [[L14-Early-Termination-Reduced-Resource-Computation]]
    * **Key Concepts:** [[reduced-resource-computation]], [[early-phase-termination]]
    * **Solution Insight:** Database commit/rollback, embedded system safe defaults

* **Sub: (g)**
    * **Topic:** Instruction reordering
    * **Lectures:** [[L06-Modern-Processors]]
    * **Key Concepts:** [[pipeline-hazards]], [[pipelining]], [[out-of-order-execution]]
    * **Solution Insight:** Filling delay slots after a branch with useful work

* **Sub: (h)**
    * **Topic:** Super-linear speedup
    * **Lectures:** [[L29-Liar-Liar]]
    * **Key Concepts:** [[profiler-lies]]
    * **Solution Insight:** Fewer-core time is artificially inflated (not a real baseline)

* **Sub: (i)**
    * **Topic:** Memory reduction
    * **Lectures:** [[L01-Programming-for-Performance]], [[L14-Early-Termination-Reduced-Resource-Computation]]
    * **Key Concepts:** [[caching]], [[reduced-resource-computation]]
    * **Solution Insight:** Throw away and recompute from remaining data when needed

* **Sub: (j)**
    * **Topic:** LLMs
    * **Lectures:** —
    * **Key Concepts:** N/A
    * **Solution Insight:** —

---

## Q2: Not-As-Short Answer (25 marks)

* **Sub: 2.1**
    * **Topic:** Compiled vs interpreted
    * **Lectures:** [[L18-Compiler-Optimizations]], [[L20-Self-Optimizing-Software]]
    * **Key Concepts:** [[compiler-optimization-levels]], [[jit-compilation]], [[link-time-optimization]]
    * **Solution Insight:** Compiled: whole-program analysis at compile time. Interpreted: runtime decisions with more info, easier adaptation

* **Sub: 2.2**
    * **Topic:** Logs and SLAs
    * **Lectures:** [[L24-Profiling-Observing-Operations]]
    * **Key Concepts:** [[logging]], [[tracing]], [[percentiles]], [[aggregate-measures]]
    * **Solution Insight:** Track call start/end times, aggregate over time, check if >5% exceed $n$ ms, account for network latency

* **Sub: 2.3**
    * **Topic:** N-Queens lock contention
    * **Lectures:** [[L12-Lock-Convoys-Atomics-Lock-Freedom]]
    * **Key Concepts:** [[atomic-operations]], [[compare-and-swap]], [[lock-contention]], [[mutex]]
    * **Solution Insight:** Option 1: atomic add. Option 2: thread-local sums, combine after join. Either is acceptable

* **Sub: 2.4**
    * **Topic:** LLMs and accuracy/time
    * **Lectures:** [[L14-Early-Termination-Reduced-Resource-Computation]]
    * **Key Concepts:** [[reduced-resource-computation]]
    * **Solution Insight:** No — LLMs are statistical, not iterative. More time doesn't improve correctness; need better model

* **Sub: 2.5A**
    * **Topic:** Jittery RDTSC
    * **Lectures:** [[L24-Profiling-Observing-Operations]]
    * **Key Concepts:** [[profiling]], [[aggregate-measures]]
    * **Solution Insight:** Measure many times, average, wait for variance to be small

* **Sub: 2.5B**
    * **Topic:** RDTSC wrong answers
    * **Lectures:** [[L06-Modern-Processors]], [[L15-Memory-Consistency]]
    * **Key Concepts:** [[out-of-order-execution]], [[memory-barriers]]
    * **Solution Insight:** OOO execution reorders around RDTSC — use fences. Also: multi-CPU TSC desync

---

## Q3: Queueing Theory (15 marks)

| Sub | Concepts | Key Formulas |
| :--- | :--- | :--- |
| 3.1 | [[mm1-queue]], [[arrival-rate-and-service-rate]], [[utilization]], [[littles-law]] | $T_q = \frac{s\rho}{1-\rho}, \rho = \lambda s, W = \frac{\rho^2}{1-\rho}$ |
| 3.2 | [[mm1-queue]], [[arrival-rate-and-service-rate]] | Reduce $\lambda$ by 20%, recalculate |
| 3.3 | [[mm1-queue]], [[saturation]], [[utilization]] | $\rho = 1.5 \rightarrow$ overloaded, impossible |
| 3.4 | [[mmk-queue]], [[one-fast-server-vs-many-slow]] | M/M/3 with Erlang C formula |

---

## Q4: Compiler Optimizations (25 marks)

* **Sub: 4.1**
    * **Concepts:** [[inlining]]
    * **Solution Insight:** Inline `square` into `sum_square`, then inline both into `main`

* **Sub: 4.2**
    * **Concepts:** [[inlining]], [[constant-propagation]], [[loop-unrolling]]
    * **Solution Insight:** Benefits: no call overhead, enables further opts, better icache. Post-inline: constant propagation $\rightarrow$ fold to 95 and 81

* **Sub: 4.3**
    * **Concepts:** [[inlining]], [[cache-misses]]
    * **Solution Insight:** Large rarely-executed function inlined into hot caller $\rightarrow$ dead code displaces hot code in instruction cache

* **Sub: 4.4**
    * **Concepts:** [[alias-and-pointer-analysis]], [[mutable-references]], [[borrowing-and-references]]
    * **Solution Insight:** Rust's `&mut` uniqueness guarantees no aliasing $\rightarrow$ safe to use temp. C: output could alias input, or be accessed by interrupt $\rightarrow$ undefined behavior

---

## Q5: GPU (25 marks)

* **Concepts confirmed:** [[cuda-device-buffers]], [[cuda-kernel-launch]], [[cuda-stream]], [[cuda-grid-sizing]], [[cuda-atomic-functions]], [[rustacuda]], [[unsafe-rust]]

---

# Updated Study Plan

### Phase 1: Compiler Optimizations (25 marks)
* [[L18-Compiler-Optimizations]]: Inlining (mechanics, benefits, dangers), constant propagation, constant folding, loop unrolling, dead code elimination
* [[L03-Rust-Borrowing-Slices-Threads-Traits]]: Borrowing and `&mut` uniqueness (needed for Q4.4 alias analysis)

### Phase 2: Queueing Theory (15 marks)
* [[L31-Introduction-to-Queueing-Theory]]: M/M/1: $T_q = \frac{s\rho}{1-\rho}, W = \frac{\rho^2}{1-\rho}, \rho = \lambda s$, Little's Law
* [[L32-Convergence-Ergodicity-Applications]]: M/M/k: Erlang C formula, know how to compute K for M/M/3
* [[L33-More-Advanced-Queueing-Theory]]: Review saturation ($\rho \ge 1$ means system is overloaded)

### Phase 3: GPU Programming (25 marks)
* [[L04-Rust-Breaking-the-Rules]]: Unsafe Rust, raw pointers (needed for Rustacuda FFI)
* [[L21-GPU-Programming]]: GPU model, CUDA kernels, blocks/grids, thread indexing
* [[L22-GPU-Programming-Continued]]: Rustacuda host code pattern: `DeviceBuffer`, `launch!`, `stream.synchronize`, `copy_to`, `atomicAdd`

### Phase 4: Rust Ownership & Borrowing (~12 marks)
* [[L02-Rust-Basics]]: Ownership, move semantics, clone costs (memory + cache impact)
* [[L03-Rust-Borrowing-Slices-Threads-Traits]]: Borrowing as alternative to clone, `&mut` uniqueness

### Phase 5: Performance Fundamentals (~12 marks)
* [[L01-Programming-for-Performance]]: Amdahl's Law (with actual calculations), profiling
* [[L06-Modern-Processors]]: Pipelining, delay slots, out-of-order execution, memory hierarchy

### Phase 6: Speculation & Reduced-Resource Computation (~12 marks)
* [[L13-Dependencies-and-Speculation]]: Dependencies, speculation, value speculation
* [[L14-Early-Termination-Reduced-Resource-Computation]]: Reduced-resource computation, early termination, recomputation tradeoff

### Phase 7: Locks & Atomics (~8 marks)
* [[L11-Use-of-Locks-Reentrancy]]: Lock granularity, coarse vs fine
* [[L12-Lock-Convoys-Atomics-Lock-Freedom]]: Atomic operations, CAS, lock-free alternatives

### Phase 8: Profiling & Measurement (~10 marks)
* [[L24-Profiling-Observing-Operations]]: Logging, tracing, aggregation, percentiles
* [[L15-Memory-Consistency]]: Memory barriers/fences (for Q2.5B)
* [[L29-Liar-Liar]]: Profiler lies, inflated baselines

**Priority order by marks:**
1. [[L18-Compiler-Optimizations]] (Q4)
2. [[L21-GPU-Programming]] + [[L22-GPU-Programming-Continued]] (Q5)
3. [[L31-Introduction-to-Queueing-Theory]] + [[L32-Convergence-Ergodicity-Applications]] + [[L33-More-Advanced-Queueing-Theory]] (Q3)
4. [[L02-Rust-Basics]] + [[L03-Rust-Borrowing-Slices-Threads-Traits]] (Q1, Q4)
5. Everything else
