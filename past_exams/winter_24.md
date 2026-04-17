# Question-by-Question Concept Mapping

## Q1: Short Answer (30 marks)

* **Sub: (a)**
    * **Topic:** Rate limits - multiple accounts
    * **Lectures:** [[L01-Programming-for-Performance]]
    * **Key Concepts:** [[bandwidth-vs-latency]], [[rate-limiting]]
    * **Solution Insight:** Arguable both ways — could be circumventing or just using more resources.

* **Sub: (b)**
    * **Topic:** Async I/O - why not sleep
    * **Lectures:** [[L04-Rust-Breaking-the-Rules]], [[L05-Asynchronous-IO]]
    * **Key Concepts:** [[async-io-and-waiting]], [[blocking-vs-non-blocking-io]], [[polling-and-event-driven-io]]
    * **Solution Insight:** Sleep wastes CPU or adds latency; use notification/polling instead.

* **Sub: (c)**
    * **Topic:** Reduced-resource computation
    * **Lectures:** [[L02-Rust-Basics]]
    * **Key Concepts:** [[reduced-resource-computation]], [[early-phase-termination]]
    * **Solution Insight:** Database commit/rollback as time-limited example.

* **Sub: (d)**
    * **Topic:** DevOps - speed up queries
    * **Lectures:** [[L02-Rust-Basics]]
    * **Key Concepts:** [[devops]], [[caching]]
    * **Solution Insight:** Archive/delete old data or add indexes — not fake accounts.

* **Sub: (e)**
    * **Topic:** Phone tree = what parallelism
    * **Lectures:** [[L09-Algorithms-Concurrency-and-Parallelism]]
    * **Key Concepts:** [[task-parallelism]], [[concurrency-vs-parallelism]]
    * **Solution Insight:** Task parallelism — different people make different calls.

* **Sub: (f)**
    * **Topic:** 64→32→16 bit floats
    * **Lectures:** [[L02-Rust-Basics]]
    * **Key Concepts:** [[reduced-resource-computation]], [[fp32-vs-fp64]]
    * **Solution Insight:** Depends on whether hardware has native 16-bit support.

* **Sub: (g)**
    * **Topic:** Stream-VByte SIMD decode
    * **Lectures:** [[L07-CPU-Hardware-Branch-Prediction]]
    * **Key Concepts:** [[simd]], [[stream-vbyte]], [[auto-vectorization]]
    * **Solution Insight:** Specific hex byte decode using shuffle/lookup table.

* **Sub: (h)**
    * **Topic:** Deleting abstraction helps compiler
    * **Lectures:** [[L06-Modern-Processors]]
    * **Key Concepts:** [[compiler-optimization-levels]], [[devirtualization]], [[inlining]]
    * **Solution Insight:** Removing superclass allows devirtualization → inlining.

* **Sub: (i)**
    * **Topic:** Causal profiling - can't do all 3
    * **Lectures:** [[L28-Causal-and-Simulation-Profiling]]
    * **Key Concepts:** [[causal-profiling]], [[coz-profiler]], [[virtual-speedup]]
    * **Solution Insight:** Time conflict between optimizations or diminishing returns.

* **Sub: (j)**
    * **Topic:** LLMs
    * **Lectures:** [[L35-DevOps-Operations]]
    * **Key Concepts:** [[large-language-models]]
    * **Solution Insight:** Open-ended.

---

## Q2: Queueing Theory (17 marks)

| Sub | Topic | Lectures | Key Concepts | Solution Insight |
| :--- | :--- | :--- | :--- | :--- |
| **2.1** | M/M/2 server analysis | [[L26-Finding-Bottleneck-Devices]] | [[mm1-queue]], [[mmk-queue]], [[kendall-notation]], [[utilization]], [[queueing-theory]] | Kendall = M/M/2, $\rho = \lambda / (k\mu)$, compute $K, T_q, W$; find max $\lambda$ and min $\mu$. |
| **2.2** | Slowdown vs response time | [[L26-Finding-Bottleneck-Devices]] | [[queueing-theory]], [[improving-latency]] | Slowdown = response/service; proportional to job size. |
| **2.3** | Disney FastPass | [[L26-Finding-Bottleneck-Devices]] | [[queueing-theory]] | Priority queue tradeoffs — shorter wait for some, longer for others. |

---

## Q3: Profiling (13 marks)

* **Sub: 3.1**
    * **Topic:** Skid in profiling
    * **Lectures:** [[L27-Program-Profiling-and-POGO]]
    * **Key Concepts:** [[profiler-lies]], [[skid]], [[cpu-profiling]], [[sampling-vs-instrumentation-profiling]]
    * **Solution Insight:** Expensive load shows low %; NOP after it shows high %. No-skid mode is expensive.

* **Sub: 3.2**
    * **Topic:** POGO optimizations
    * **Lectures:** [[L27-Program-Profiling-and-POGO]], [[L06-Modern-Processors]]
    * **Key Concepts:** [[pogo-optimizations]], [[profile-guided-optimization]], [[register-renaming]], [[loop-unrolling]], [[auto-vectorization]]
    * **Solution Insight:** Register alloc reduces memory access; exception separation improves icache; loop vectorization uses SIMD.

---

## Q4: Rust (20 marks)

* **Sub: 4.1**
    * **Topic:** Lifetime annotations
    * **Lectures:** [[L14-Early-Termination-Reduced-Resource-Computation]], [[L15-Memory-Consistency]]
    * **Key Concepts:** [[lifetimes]], [[borrowing-and-references]], [[ownership]]
    * **Solution Insight:** Add `'a` to return type and parameter `x`.

* **Sub: 4.2**
    * **Topic:** Multithreaded atomic counter
    * **Lectures:** [[L14-Early-Termination-Reduced-Resource-Computation]], [[L15-Memory-Consistency]], [[L10-Software-Architecture]]
    * **Key Concepts:** [[rust-threads]], [[fearless-concurrency]], [[atomic-operations]], [[memory-consistency-models]], [[acquire-release-ordering]], [[relaxed-ordering]]
    * **Solution Insight:** Use scoped threads, Arc; Relaxed ordering bug — counter not guaranteed visible; fix with Acquire/Release.

---

## Q5: CUDA (20 marks)

* **Sub: 5a**
    * **Topic:** Naive matrix multiply kernel
    * **Lectures:** [[L22-GPU-Programming-Continued]], [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]
    * **Key Concepts:** [[cuda]], [[gpu-programming-model]], [[cuda-kernel]], [[cuda-blocks-and-grids]]
    * **Solution Insight:** `row = blockIdx.y * blockDim.y + threadIdx.y`, `col = ...x`, dot product loop.

* **Sub: 5b**
    * **Topic:** Blocked/shared memory version
    * **Lectures:** [[L22-GPU-Programming-Continued]], [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]
    * **Key Concepts:** [[gpu-shared-memory]], [[data-layout-and-alignment]], [[gpu-memory-hierarchy]]
    * **Solution Insight:** Load tile to shared memory, `__syncthreads` before compute AND before next tile load. Reduces global reads from 2048 to 128.

---

## Q6: Caching with MESI (20 marks)

* **Sub: 6**
    * **Topic:** Distributed cache using MESI states
    * **Lectures:** [[L19-Query-Optimization]], [[L20-Self-Optimizing-Software]]
    * **Key Concepts:** [[mesi-protocol]], [[cache-coherency]], [[write-back-cache]], [[invalidation-vs-update]], [[distributed-cache-software]]
    * **Solution Insight:** Map MESI states to distributed software cache: Modified = dirty local copy, Exclusive = only copy, Shared = multiple readers, Invalid = stale. Full state machine for get/update/invalidate/join/leave.

---

# W24 Study Plan (Priority Order)

### Tier 1 — Highest Weight (covers ~60% of marks)
1.  **CUDA Kernels ([[L22-GPU-Programming-Continued]], [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]) — 20 marks**
    * Thread indexing (blockIdx, blockDim, threadIdx)
    * Naive matrix multiply kernel
    * Shared memory tiling with `__syncthreads`
2.  **Rust Ownership & Concurrency ([[L14-Early-Termination-Reduced-Resource-Computation]], [[L15-Memory-Consistency]]) — 20 marks**
    * Lifetime annotation rules
    * Spawning threads with `std::thread::scope`
    * Atomics: `AtomicUsize` with `fetch_add` and memory ordering
3.  **Cache Coherence / MESI ([[L19-Query-Optimization]], [[L20-Self-Optimizing-Software]]) — 20 marks**
    * Four MESI states and transitions
    * Applying MESI to software distributed caches

### Tier 2 — Medium Weight (~25% of marks)
4.  **Queueing Theory ([[L26-Finding-Bottleneck-Devices]]) — 17 marks**
    * M/M/1 and M/M/k formulas ($\rho, T_q, W, K$)
    * Stability condition ($\rho < 1$) and slowdown metric
5.  **Profiling ([[L27-Program-Profiling-and-POGO]], [[L28-Causal-and-Simulation-Profiling]]) — 13 marks**
    * Skid: why sampled instruction $\neq$ costly instruction
    * POGO and Causal profiling (virtual speedup)

### Tier 3 — Short Answer Breadth (~15% of marks)
6.  **Quick Concept Pass:**
    * Async I/O ([[L04-Rust-Breaking-the-Rules]], [[L05-Asynchronous-IO]])
    * SIMD / Stream-VByte ([[L07-CPU-Hardware-Branch-Prediction]])
    * Compiler optimizations ([[L06-Modern-Processors]])
