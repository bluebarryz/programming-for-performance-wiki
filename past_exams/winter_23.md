# Question-by-Question Concept Mapping

Note: W23 was a take-home, open-book exam. Q1-Q2 are written; Q3-Q6 are programming questions.

## Q1: Short Answer (30 marks)

* **Sub: (a)**
    * **Topic:** Concurrency problem Rust can't prevent
    * **Lectures:** [[L11-Use-of-Locks-Reentrancy]], [[L03-Rust-Borrowing-Slices-Threads-Traits]]
    * **Key Concepts:** [[deadlock]], [[ownership]], [[locking-and-synchronization]]
    * **Solution Insight:** Deadlock — Rust prevents data races but not lock-ordering problems. Thread 1 locks A then B, thread 2 locks B then A → deadlock.

* **Sub: (b)**
    * **Topic:** Leader election as reduced-resource computation
    * **Lectures:** [[L14-Early-Termination-Reduced-Resource-Computation]]
    * **Key Concepts:** [[reduced-resource-computation]], [[early-phase-termination]]
    * **Solution Insight:** Database leader election: ends as soon as a majority is reached rather than waiting for all servers to respond.

* **Sub: (c)**
    * **Topic:** Speedup calculation — 4→6 CPUs vs reduce sequential 3%
    * **Lectures:** [[L01-Programming-for-Performance]], [[L09-Algorithms-Concurrency-and-Parallelism]]
    * **Key Concepts:** [[amdahls-law]], [[parallelism]], [[gustafsons-law]]
    * **Solution Insight:** Original speedup 2.454. With 6 CPUs: 2.927. With 3% less sequential (dev): 2.597. More CPUs wins.

* **Sub: (d)**
    * **Topic:** Speculation in N-body problem
    * **Lectures:** [[L13-Dependencies-and-Speculation]]
    * **Key Concepts:** [[speculative-execution]], [[value-speculation]], [[n-body-problem]]
    * **Solution Insight:** Assume most points are far away, subtract close ones. Was even recommended in an assignment.

* **Sub: (e)**
    * **Topic:** Detecting abuse of a free service
    * **Lectures:** [[L24-Profiling-Observing-Operations]], [[L27-Program-Profiling-and-POGO]]
    * **Key Concepts:** [[profiling]], [[logging]], [[monitoring-and-alerting]]
    * **Solution Insight:** Use monitoring/logging to find outliers (accounts with excessive CPU/resources), then investigate with profiling tools.

* **Sub: (f)**
    * **Topic:** Order of magnitude estimation — Mutex lock/unlock timing
    * **Lectures:** [[L25-Load-Testing]]
    * **Key Concepts:** [[load-testing]], [[mutex]], [[lock-contention]]
    * **Solution Insight:** Alter `MAX` as needed and measure with `hyperfine`. Single-threaded mutex lock+unlock+increment.

* **Sub: (g)**
    * **Topic:** Queueing theory — time average for aperiodic system
    * **Lectures:** [[L31-Introduction-to-Queueing-Theory]], [[L32-Convergence-Ergodicity-Applications]]
    * **Key Concepts:** [[queueing-theory]], [[ergodicity]]
    * **Solution Insight:** If samples are sufficiently random, time average works. System must be aperiodic to avoid sampling bias — breaking the link between sample time and sampled value.

* **Sub: (h)**
    * **Topic:** Causal profiling — speeding up a part makes things worse
    * **Lectures:** [[L28-Causal-and-Simulation-Profiling]]
    * **Key Concepts:** [[causal-profiling]], [[coz-profiler]], [[virtual-speedup]]
    * **Solution Insight:** Database rollbacks — if the now-faster part causes other transactions to be rolled back and restarted, overall performance worsens.

* **Sub: (i)**
    * **Topic:** Interchangeability of courses in a degree
    * **Lectures:** —
    * **Key Concepts:** N/A
    * **Solution Insight:** Spectrum of interchangeability — electives are partially interchangeable, some courses have no substitutes.

* **Sub: (j)**
    * **Topic:** Strength reduction — compiler optimization
    * **Lectures:** [[L18-Compiler-Optimizations]]
    * **Key Concepts:** [[induction-variable-elimination]], [[compiler-optimization-levels]]
    * **Solution Insight:** Replace expensive operation with cheaper equivalent. E.g., `x *= 2` → `x = x + x` since addition is cheaper than multiplication.

---

## Q2: Compilers vs Software Engineers (20 marks)

* **Sub: 2a (10 marks)**
    * **Topic:** Manual optimizations compilers can't do + one compiler-only optimization
    * **Lectures:** [[L18-Compiler-Optimizations]], [[L06-Modern-Processors]]
    * **Key Concepts:** [[compiler-optimization-levels]], [[inlining]], [[devirtualization]], [[loop-unrolling]], [[auto-vectorization]], [[register-renaming]]
    * **Solution Insight:** Pick 3 manual Rust optimizations from L18/referenced materials, explain why compiler can't automate them. Name one compiler-only opt (e.g., register allocation at source level).

* **Sub: 2b (10 marks)**
    * **Topic:** Common patterns across compiler optimizations
    * **Lectures:** [[L18-Compiler-Optimizations]]
    * **Key Concepts:** [[inlining]], [[loop-unrolling]], [[loop-fusion-and-fission]], [[devirtualization]], [[tail-recursion-elimination]], [[constant-propagation]]
    * **Solution Insight:** Three patterns: (1) reduce function call overhead — inlining, devirtualization, tail call elimination; (2) improve locality/cache — inlining, loop unrolling, loop fusion; (3) specializing for a particular case.

---

## Q3: Buffering (10 marks)

* **Topic:** Implement `Flush` trait for a `Buffer` in Rust
* **Lectures:** [[L03-Rust-Borrowing-Slices-Threads-Traits]], [[L05-Asynchronous-IO]]
* **Key Concepts:** [[traits]], [[borrowing-and-references]], [[mutex]]
* **Solution Insight:** Implement `add_to_buffer` (copy bytes, flush when full), `flush` (write to file, reset index), `do_flush` (lock destination, write, clear array). Test with `hyperfine` at different `BUFFER_SIZE` values using debug vs release builds.

---

## Q4: Rust Fundamentals (10 marks)

* **Sub: 4a (5 marks)**
    * **Topic:** Removing `.clone()` calls
    * **Lectures:** [[L02-Rust-Basics]], [[L03-Rust-Borrowing-Slices-Threads-Traits]]
    * **Key Concepts:** [[ownership]], [[move-semantics]], [[borrowing-and-references]]
    * **Solution Insight:** Rewrite `S::new` to take ownership via indexing or use `&str` references instead of cloning `String`s.

* **Sub: 4b (5 marks)**
    * **Topic:** Lifetime annotations
    * **Lectures:** [[L03-Rust-Borrowing-Slices-Threads-Traits]], [[L04-Rust-Breaking-the-Rules]]
    * **Key Concepts:** [[lifetimes]], [[borrowing-and-references]]
    * **Solution Insight:** Add lifetime annotations to `f` so the return type borrows from the correct parameter. Cannot change `g`'s signature or remove `'static` on `rv`.

---

## Q5: Password Cracking (10 marks)

* **Topic:** Parallelize rainbow table building with Rayon
* **Lectures:** [[L17-Mostly-Data-Parallelism]], [[L23-Password-Cracking-Bitcoin-Mining-LLMs]]
* **Key Concepts:** [[data-parallelism]], [[task-parallelism]], [[password-cracking]], [[rainbow-tables]]
* **Solution Insight:** Use `par_iter_mut()` from Rayon to parallelize both the initial hash and the reduce-and-hash chain loops. MD5 hashing of 6-digit passwords.

---

## Q6: Typst Compiler Optimization (20 marks)

* **Sub: 6.1 (5 marks)**
    * **Topic:** Identifying optimization targets from flamegraph
    * **Lectures:** [[L27-Program-Profiling-and-POGO]], [[L28-Causal-and-Simulation-Profiling]]
    * **Key Concepts:** [[flamegraph]], [[cpu-profiling]], [[causal-profiling]], [[amdahls-law]]
    * **Solution Insight:** Two largest components under `counter::Counter::at`: `query_before` (18.24%) and `sequence` (38.30%). Max speedup: $100/(100-18.24) = 1.22\times$ and $100/(100-38.30) = 1.62\times$ respectively (Amdahl's Law).

* **Sub: 6.2 (15 marks)**
    * **Topic:** Explain and optimize comemo memoization in Typst
    * **Lectures:** [[L18-Compiler-Optimizations]], [[L20-Self-Optimizing-Software]]
    * **Key Concepts:** [[caching]], [[profiling]]
    * **Solution Insight:** `query_before` returns `Vec<Content>` but callers only use `.len()`. Optimization: return `usize` instead of `Vec`, avoiding cloning elements. Speedup from 8s to 5s. The `comemo` crate hashes return values for memoization — smaller return = faster hash.

---

# W23 Study Plan (Priority Order)

### Tier 1 — Highest Weight (covers ~40% of marks)

1. **Compiler Optimizations ([[L18-Compiler-Optimizations]]) — 20 marks (Q2) + 3 marks (Q1j)**
    * Manual vs compiler optimizations — know which can't be automated
    * Patterns: reducing call overhead, improving locality, specialization
    * Specific optimizations: [[inlining]], [[devirtualization]], [[loop-unrolling]], [[loop-fusion-and-fission]], [[induction-variable-elimination]], [[tail-recursion-elimination]]

2. **Profiling & Optimization ([[L27-Program-Profiling-and-POGO]], [[L28-Causal-and-Simulation-Profiling]]) — 20 marks (Q6) + 3 marks (Q1e)**
    * Reading flamegraphs and identifying bottlenecks
    * Applying Amdahl's Law to profiling data for max speedup
    * [[caching]] / memoization as an optimization strategy

### Tier 2 — Medium Weight (~20% of marks)

3. **Rust Ownership & Lifetimes ([[L02-Rust-Basics]], [[L03-Rust-Borrowing-Slices-Threads-Traits]]) — 10 marks (Q4) + 10 marks (Q3)**
    * Removing `.clone()` by using references or ownership transfer
    * Lifetime annotations — when return borrows from parameter
    * Implementing traits (`Flush`), working with `Mutex`

### Tier 3 — Moderate Weight (~10% of marks)

4. **Parallelism with Rayon ([[L17-Mostly-Data-Parallelism]]) — 10 marks (Q5)**
    * `par_iter_mut()` for data-parallel workloads
    * Password cracking / rainbow tables as parallelizable problem

### Tier 4 — Short Answer Breadth (~30% of marks)

5. **Quick Concept Pass:**
    * Deadlock ([[L11-Use-of-Locks-Reentrancy]]): Rust prevents data races, not deadlocks
    * Amdahl's Law ([[L01-Programming-for-Performance]]): actual speedup calculations
    * Speculation ([[L13-Dependencies-and-Speculation]]): N-body approximation
    * Causal profiling ([[L28-Causal-and-Simulation-Profiling]]): negative speedup scenarios
    * Queueing theory ([[L31-Introduction-to-Queueing-Theory]]): ergodicity and time averages
    * [[load-testing]] ([[L25-Load-Testing]]): order-of-magnitude estimation with `hyperfine`
