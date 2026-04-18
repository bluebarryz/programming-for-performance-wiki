---
tags:
  - index
  - ece459
---

# ECE 459: Programming for Performance — Wiki Index

> 35 lectures, 365 concepts. Use Obsidian's graph view to explore connections.

## Lectures

| # | Lecture | Key Themes |
|---|--------|------------|
| 01 | [[L01-Programming-for-Performance]] | Performance fundamentals, bandwidth vs latency, Amdahl's Law |
| 02 | [[L02-Rust-Basics]] | Ownership, move semantics, memory management |
| 03 | [[L03-Rust-Borrowing-Slices-Threads-Traits]] | Borrowing, threads, traits, Send/Sync |
| 04 | [[L04-Rust-Breaking-the-Rules]] | Unsafe Rust, smart pointers, interior mutability |
| 05 | [[L05-Asynchronous-IO]] | Async I/O, futures, tokio, event loops |
| 06 | [[L06-Modern-Processors]] | Pipelining, ILP, memory hierarchy, NUMA |
| 07 | [[L07-CPU-Hardware-Branch-Prediction]] | Branch prediction, speculative execution |
| 08 | [[L08-Cache-Coherency]] | Cache protocols (MSI/MESI/MESIF), false sharing |
| 09 | [[L09-Algorithms-Concurrency-and-Parallelism]] | Amdahl's & Gustafson's Laws, thread pools |
| 10 | [[L10-Software-Architecture]] | Monolith vs microservices, N+1 queries |
| 11 | [[L11-Use-of-Locks-Reentrancy]] | Lock granularity, deadlock, reentrancy |
| 12 | [[L12-Lock-Convoys-Atomics-Lock-Freedom]] | Lock convoys, CAS, lock-free structures |
| 13 | [[L13-Dependencies-and-Speculation]] | Dependencies, speculation, critical path |
| 14 | [[L14-Early-Termination-Reduced-Resource-Computation]] | Early termination, loop perforation, approximation |
| 15 | [[L15-Memory-Consistency]] | Memory ordering, barriers, acquire/release |
| 16 | [[L16-Rate-Limits]] | Rate limiting, throttling, exponential backoff |
| 17 | [[L17-Mostly-Data-Parallelism]] | SIMD, SSE/AVX, auto-vectorization |
| 18 | [[L18-Compiler-Optimizations]] | Inlining, loop opts, constant folding, LTO |
| 19 | [[L19-Query-Optimization]] | Query plans, join ordering, cost estimation |
| 20 | [[L20-Self-Optimizing-Software]] | JIT, escape analysis, genetic algorithms |
| 21 | [[L21-GPU-Programming]] | CUDA, GPU architecture, kernels |
| 22 | [[L22-GPU-Programming-Continued]] | Shared memory, warps, branching on GPUs |
| 23 | [[L23-Password-Cracking-Bitcoin-Mining-LLMs]] | Cryptographic hashing, mining, LLM training |
| 24 | [[L24-Profiling-Observing-Operations]] | Observability, logging, tracing, counters |
| 25 | [[L25-Load-Testing]] | Load/stress/endurance testing |
| 26 | [[L26-Finding-Bottleneck-Devices]] | CPU/memory/disk/network/lock bottlenecks |
| 27 | [[L27-Program-Profiling-and-POGO]] | Sampling, instrumentation, POGO |
| 28 | [[L28-Causal-and-Simulation-Profiling]] | Coz, causal profiling, simulation profiling |
| 29 | [[L29-Liar-Liar]] | Profiler lies, skid, aliasing, distortion |
| 30 | [[L30-Clusters-Cloud-Computing]] | MPI, Kafka, cloud computing, COST paper |
| 31 | [[L31-Introduction-to-Queueing-Theory]] | Little's Law, M/M/1, Kendall notation |
| 32 | [[L32-Convergence-Ergodicity-Applications]] | Convergence, ergodicity, load balancing |
| 33 | [[L33-More-Advanced-Queueing-Theory]] | Balking, reneging, priority queues, simulation |
| 34 | [[L34-DevOps-Configuration]] | CI, IaC, Terraform, Kubernetes, canary deploys |
| 35 | [[L35-DevOps-Operations]] | Monitoring, alerting, incident response, security |

---

## Concepts by Topic

### Performance Fundamentals (L01)
- [[bandwidth-vs-latency]] — Items/time vs time/item
- [[improving-latency]] — Profile, do less work, be smarter, cache
- [[scalability]] — Performance under increasing load
- [[amdahls-law]] — Speedup limited by serial fraction
- [[parallelism]] — Doing multiple things at once
- [[pipelining]] — Splitting tasks into overlapping stages
- [[embarrassingly-parallel]] — Problems with no inter-task dependencies
- [[data-races]] — Concurrent unsynchronized access
- [[deadlocks]] — Circular resource waiting
- [[dependencies-in-parallelism]] — What limits parallelization
- [[caching]] — Reusing expensive computation results
- [[profiling]] — Measuring where time is spent
- [[laws-of-performant-software]] — Crista's five laws
- [[premature-optimization]] — Don't guess; measure

### Rust Language (L02-L04)
- [[rust-motivation]] — Why Rust for performance
- [[ownership]] — Single-owner memory model
- [[move-semantics]] — Transfer of ownership
- [[rust-memory-management]] — No GC, compile-time safety
- [[garbage-collection-vs-ownership]] — Rust vs GC languages
- [[raii]] — Resource cleanup via Drop
- [[copy-and-drop-traits]] — Bitwise copy vs move
- [[immutability-by-default]] — Variables immutable unless `mut`
- [[shadowing]] — Rebinding variable names
- [[borrow-checker]] — Compile-time reference validation
- [[borrowing-and-references]] — Using data without ownership
- [[mutable-references]] — Exclusive `&mut` access
- [[non-lexical-lifetimes]] — Borrows end at last use
- [[slices]] — Views into contiguous data
- [[result-and-error-handling]] — `Result<T, E>` and `?` operator
- [[traits]] — Interface-like abstractions
- [[iterator-trait]] — Lazy iteration protocol
- [[closures-and-capturing]] — Anonymous functions capturing environment
- [[move-keyword]] — Force ownership transfer into closures
- [[fearless-concurrency]] — Compile-time thread safety
- [[rust-threads]] — `std::thread::spawn` and join
- [[message-passing-channels]] — `mpsc` for thread communication
- [[send-trait]] — Safe to transfer across threads
- [[sync-trait]] — Safe to share references across threads
- [[mutex]] — Mutual exclusion wrapping a value
- [[box-smart-pointer]] — Heap allocation
- [[rc-reference-counting]] — Single-threaded shared ownership
- [[arc-atomic-reference-counting]] — Thread-safe shared ownership
- [[lifetimes]] — Reference validity annotations
- [[static-lifetime]] — `'static` lifetime
- [[unsafe-rust]] — Escape hatch for unsafe operations
- [[mutable-static-variables]] — Global mutable state (unsafe)
- [[unions]] — C-style unions (unsafe access)
- [[raw-pointers]] — `*const T` / `*mut T` for FFI
- [[rust-pitfalls]] — Common mistakes (clone abuse, unwrap, etc.)

### Asynchronous I/O (L05)
- [[blocking-vs-non-blocking-io]] — Blocking wastes CPU cycles
- [[polling-and-event-driven-io]] — select/poll/epoll
- [[callbacks]] — Functions invoked on events
- [[concurrent-server-architectures]] — Four server models
- [[libcurl-easy-and-multi]] — Sync vs async curl interfaces
- [[mio-event-loop]] — Cross-platform event loop
- [[futures-and-async-await]] — Deferred values with async/await
- [[tokio-runtime]] — Async runtime built on mio

### Modern Processors & Hardware (L06-L08)
- [[von-neumann-architecture]] — Fetch-decode-execute cycle
- [[cpu-memory-gap]] — CPU speed outpacing memory
- [[memory-hierarchy]] — Registers, L1, L2, L3, RAM, disk
- [[sram-vs-dram]] — Fast/expensive vs slow/cheap memory
- [[effective-access-time]] — Weighted average by hit rates
- [[pipelining]] — Overlapping instruction stages
- [[pipeline-hazards]] — Data, control, structural hazards
- [[instruction-level-parallelism]] — Multiple instructions per cycle
- [[dual-issue]] — Executing two instructions simultaneously
- [[out-of-order-execution]] — CPU reordering for efficiency
- [[register-renaming]] — Eliminating false dependencies
- [[cisc-vs-risc]] — Complex vs reduced instruction sets
- [[frequency-scaling]] — Clock speed history and limits
- [[multicore-processors]] — Multiple cores per chip
- [[symmetric-multiprocessing]] — Shared-memory multiprocessor
- [[non-uniform-memory-access]] — Non-uniform memory latency
- [[hyperthreading]] — Two threads per physical core
- [[branch-prediction]] — Guessing branch outcomes
- [[static-branch-prediction]] — Heuristics (backward taken, forward not)
- [[dynamic-branch-prediction]] — History-based prediction
- [[two-bit-saturating-counter]] — Basic dynamic predictor
- [[two-level-adaptive-predictor]] — Pattern-based prediction
- [[gshare-predictor]] — XOR of history and address
- [[branch-prediction-performance-model]] — Calculating mispredict cost
- [[likely-unlikely-hints]] — Compiler hints for branches
- [[speculation]] — Executing before knowing outcome
- [[spectre-and-meltdown]] — Speculation-based attacks
- [[side-channel-attacks]] — Leaking info via timing
- [[miss-shadow]] — Overlapping cache miss latency
- [[cache-misses]] — Compulsory, capacity, conflict, coherence
- [[cache-coherency]] — Keeping caches consistent
- [[snoopy-caches]] — Bus-snooping protocol
- [[write-through-cache]] — Write to cache and memory
- [[write-back-cache]] — Write to cache, defer memory
- [[msi-protocol]] — Modified/Shared/Invalid
- [[mesi-protocol]] — MSI + Exclusive state
- [[mesif-protocol]] — MESI + Forward state
- [[invalidation-vs-update]] — Two coherence strategies
- [[false-sharing]] — Cache line contention on unrelated data
- [[distributed-cache-software]] — memcached, Redis

### Algorithms, Concurrency & Architecture (L09-L10)
- [[concurrency-vs-parallelism]] — Interleaving vs simultaneous execution
- [[amdahls-law]] — Serial fraction limits speedup
- [[gustafsons-law]] — Scale problem size with cores
- [[parallelization-overhead]] — Communication, synchronization costs
- [[thread-pools]] — Reusing threads to reduce overhead
- [[locking-and-synchronization]] — Coordinating shared access
- [[memory-allocators]] — malloc contention in parallel code
- [[accidentally-quadratic]] — Hidden O(n^2) in data structures
- [[algorithm-optimization]] — Better algorithms over micro-opts
- [[system-design]] — High-level architecture decisions
- [[monolith-vs-microservices]] — Architectural tradeoffs
- [[complexity-and-abstraction]] — Layering costs
- [[excessive-network-calls]] — Chattiness kills performance
- [[n-plus-one-query]] — 1 query + N follow-up queries
- [[eager-loading]] — Prefetching related data
- [[graphql]] — Flexible query language for APIs
- [[architectural-bottlenecks]] — Design-level performance issues
- [[over-taking-responsibility]] — Services doing too much
- [[async-io-and-waiting]] — Don't block waiting for I/O
- [[lock-contention]] — Threads waiting for locks

### Locks & Atomics (L11-L12)
- [[locking-granularity]] — Coarse vs fine-grained locks
- [[coarse-grained-locking]] — One big lock (simple but slow)
- [[fine-grained-locking]] — Many locks (faster but complex)
- [[critical-section-sizing]] — Keep locked regions small
- [[lock-overhead]] — Cost of acquiring/releasing locks
- [[lock-contention]] — Threads competing for the same lock
- [[deadlock]] — Four conditions (Coffman)
- [[reentrancy]] — Functions safe to call recursively/concurrently
- [[global-interpreter-lock]] — Python's GIL limiting parallelism
- [[lock-convoys]] — Threads queuing behind a slow holder
- [[unfair-locks]] — Non-FIFO lock acquisition
- [[thundering-herd-problem]] — All waiters waking at once
- [[lost-wakeup-problem]] — Missed notifications
- [[spinlock]] — Busy-wait locking
- [[trylock]] — Non-blocking lock attempt
- [[atomic-operations]] — Hardware-supported indivisible operations
- [[compare-and-swap]] — CAS: the foundation of lock-free code
- [[aba-problem]] — CAS hazard with recycled values
- [[lock-free-data-structures]] — Progress guaranteed system-wide
- [[wait-free-data-structures]] — Progress guaranteed per-thread
- [[non-blocking-data-structures]] — General non-blocking category
- [[pure-functions]] — No side effects, naturally parallelizable
- [[side-effects]] — Observable state changes
- [[functional-programming-and-parallelization]] — FP enables parallelism

### Dependencies & Speculation (L13-L14)
- [[dependencies]] — True, anti, and output dependencies
- [[loop-carried-dependencies]] — Cross-iteration dependencies
- [[memory-carried-dependencies]] — Dependencies through memory
- [[critical-path]] — Longest dependency chain
- [[speculative-execution]] — Execute before dependencies resolve
- [[value-speculation]] — Guess values, verify later
- [[software-transactional-memory]] — Optimistic concurrency
- [[early-phase-termination]] — Kill slow/unnecessary work
- [[reduced-resource-computation]] — Trade precision for speed
- [[fast-inverse-square-root]] — Quake III's bit trick
- [[loop-perforation]] — Skip iterations, scale results
- [[n-body-problem]] — Gravitational simulation optimization

### Memory Consistency (L15)
- [[memory-consistency-models]] — Rules for memory operation ordering
- [[sequential-consistency]] — Strongest (and most expensive) ordering
- [[acquire-release-ordering]] — Ordering for critical sections
- [[relaxed-ordering]] — Weakest ordering (counters only)
- [[memory-barriers]] — Hardware fences preventing reordering
- [[compiler-reordering]] — Compiler rearranging instructions
- [[hardware-reordering]] — CPU reordering at runtime

### Rate Limiting (L16)
- [[rate-limiting]] — Controlling request throughput
- [[request-throttling]] — Capping concurrent requests
- [[request-grouping]] — Batching similar requests
- [[exponential-backoff]] — Increasing wait on retries
- [[jitter]] — Randomizing backoff to avoid thundering herd
- [[denial-of-service]] — Overwhelming a service with requests

### Data Parallelism (L17)
- [[data-parallelism]] — Same operation on many data items
- [[task-parallelism]] — Different operations in parallel
- [[simd]] — Single instruction, multiple data
- [[sse-and-avx]] — x86 SIMD instruction sets
- [[auto-vectorization]] — Compiler generating SIMD code
- [[data-layout-and-alignment]] — Memory alignment for SIMD
- [[vbyte-encoding]] — Variable-byte integer compression
- [[stream-vbyte]] — SIMD-accelerated VByte decoding
- [[inverted-indexes]] — Term-to-document mappings

### Compiler Optimizations (L18)
- [[compiler-optimization-levels]] — -O0 through -O3, -Os
- [[constant-folding]] — Evaluate constants at compile time
- [[constant-propagation]] — Replace variables with known constants
- [[copy-propagation]] — Replace copies with originals
- [[common-subexpression-elimination]] — Avoid redundant computation
- [[dead-code-elimination]] — Remove unreachable code
- [[induction-variable-elimination]] — Simplify loop counters
- [[scalar-replacement]] — Replace array accesses with scalars
- [[loop-optimizations]] — General loop transformation category
- [[loop-unrolling]] — Reduce loop overhead by replicating body
- [[loop-fusion-and-fission]] — Combining/splitting loops
- [[loop-interchange]] — Reorder nested loop indices
- [[loop-invariant-code-motion-aka-hoisting]] — Hoist invariant code out of loops
- [[inlining]] — Replace call with function body
- [[devirtualization]] — Resolve virtual calls at compile time
- [[alias-and-pointer-analysis]] — Determine pointer targets
- [[call-graphs]] — Function call relationships
- [[link-time-optimization]] — Whole-program optimization
- [[tail-recursion-elimination]] — Convert tail recursion to iteration

### Query Optimization (L19)
- [[relational-algebra]] — Formal query representation
- [[query-execution-plans]] — Annotated evaluation sequences
- [[query-cost-estimation]] — Estimating I/O costs
- [[database-metadata-and-histograms]] — Statistics for cost estimation
- [[equivalence-rules]] — Expression rewriting rules
- [[early-selection-and-projection]] — Reduce data early
- [[join-ordering]] — Optimal join sequence
- [[join-elimination]] — Remove unnecessary joins
- [[plan-caching]] — Reuse compiled query plans

### Self-Optimizing Software (L20)
- [[jit-compilation]] — Bytecode to native at runtime
- [[on-stack-replacement]] — Hot-swap running methods
- [[escape-analysis]] — Determine object visibility scope
- [[lock-elision-and-coarsening]] — JIT lock optimizations
- [[observe-and-change]] — Adapt config based on runtime data
- [[genetic-algorithms]] — Evolutionary parameter tuning
- [[binary-rewriting]] — Modify compiled code at runtime
- [[intrinsics]] — Platform-specific compiled operations

### GPU Programming (L21-L23)
- [[gpu-programming-model]] — Host/device split architecture
- [[heterogeneous-programming]] — CPU + GPU together
- [[cuda]] — NVIDIA's GPU programming platform
- [[opencl]] — Cross-vendor GPU standard
- [[cuda-kernel]] — Function running on GPU threads
- [[cuda-block]] — Thread group sharing memory and synchronization
- [[cuda-blocks-and-grids]] — Thread organization hierarchy
- [[cuda-grid-sizing]] — Choosing blocks and threads
- [[cuda-kernel-launch]] — Host-side kernel invocation
- [[cuda-device-and-global-functions]] — GPU function types
- [[cuda-device-buffers]] — GPU memory allocation
- [[cuda-host-code]] — CPU-side management code
- [[cuda-context]] — GPU state container
- [[cuda-module]] — Compiled GPU code container
- [[cuda-stream]] — Ordered GPU operation queue
- [[cuda-atomic-functions]] — Atomic ops on GPU
- [[gpu-memory-hierarchy]] — Global, shared, local, registers
- [[gpu-shared-memory]] — Fast per-block scratchpad
- [[gpu-warps]] — 32-thread SIMT execution units
- [[gpu-branching]] — Warp divergence on branches
- [[gpu-loop-unrolling]] — Unrolling for GPU performance
- [[simt]] — Single instruction, multiple threads
- [[nvcc-compiler]] — NVIDIA CUDA compiler
- [[ptx]] — CUDA intermediate representation
- [[rustacuda]] — Rust bindings for CUDA
- [[device-copy-trait]] — Rustacuda's DeviceCopy marker
- [[fp32-vs-fp64]] — Float precision performance gap on GPUs
- [[work-items-and-index-space]] — OpenCL execution model

### GPU Applications: Crypto & LLMs (L23)
- [[password-cracking]] — GPU-accelerated password attacks
- [[cryptographic-hashing]] — SHA, bcrypt, scrypt
- [[scrypt]] — Memory-hard password hashing
- [[memory-hard-functions]] — Resist GPU/ASIC acceleration
- [[rainbow-tables]] — Precomputed hash chains
- [[bitcoin-mining]] — SHA-256 proof of work
- [[asic-miners]] — Specialized mining hardware
- [[large-language-models]] — LLM architecture and scale
- [[llm-training-optimization]] — Techniques for faster training
- [[batch-size]] — Samples per gradient update
- [[gradient-accumulation]] — Simulate large batches
- [[gradient-checkpointing]] — Trade compute for memory
- [[mixed-precision-training]] — FP16/FP32 hybrid training
- [[data-preloading]] — Overlap data loading with compute

### Profiling & Observability (L24-L25)
- [[observability]] — Understanding system behavior
- [[logging]] — Text event recording
- [[tracing]] — Following requests across components
- [[tracing-overhead]] — Performance cost of tracing
- [[counters]] — Numeric event tracking
- [[aggregate-measures]] — Mean, median, percentiles
- [[percentiles]] — p50, p95, p99 latency
- [[dashboards]] — Visual metric displays
- [[valgrind]] — Dynamic analysis framework
- [[premature-optimization]] — Knuth: measure first
- [[load-testing]] — Testing under expected load
- [[stress-testing]] — Testing beyond capacity
- [[endurance-testing]] — Testing over extended time
- [[load-testing-planning]] — Defining load test parameters
- [[load-testing-principles]] — Best practices for load tests
- [[evaluating-load-test-success]] — Interpreting results
- [[constant-vigilance]] — Ongoing performance monitoring

### Bottleneck Analysis & Advanced Profiling (L26-L29)
- [[bottleneck-analysis]] — Identifying the limiting resource
- [[cpu-load-average]] — Interpreting load average
- [[cpu-profiling]] — CPU-focused profiling tools
- [[memory-bottleneck-diagnosis]] — Diagnosing memory issues
- [[swap-and-paging]] — Virtual memory performance impact
- [[disk-bottleneck-diagnosis]] — I/O bottleneck detection
- [[network-bottleneck-diagnosis]] — Network performance issues
- [[network-latency-vs-bandwidth]] — Diagnosis distinction
- [[lock-contention-diagnosis]] — Finding lock bottlenecks
- [[sampling-vs-instrumentation-profiling]] — Two profiling approaches
- [[instrumentation-vs-sampling-tradeoffs]] — Accuracy vs overhead
- [[invasive-profiling]] — Profiling that alters behavior
- [[perf-tool]] — Linux perf profiler
- [[flamegraph]] — Stack trace visualization
- [[hot-and-cold-code]] — Frequently vs rarely executed paths
- [[call-graph-path-profiling]] — Tracking call chains
- [[page-locality]] — Memory access patterns
- [[profiling-best-practices]] — Guidelines for effective profiling
- [[profile-guided-optimization]] — Using profiles to optimize
- [[pogo-optimizations]] — POGO-specific optimizations
- [[pogo-probes]] — Instrumentation points for POGO
- [[pogo-training]] — Generating profile data
- [[causal-profiling]] — Predicting optimization impact
- [[coz-profiler]] — Causal profiling tool
- [[virtual-speedup]] — Simulating speedup by slowing others
- [[scoz]] — System-wide causal profiling
- [[cachegrind]] — Cache simulation profiler
- [[simulation-profiling]] — Profiling via simulation
- [[miri]] — Rust MIR interpreter for analysis
- [[profiler-lies]] — Ways profilers mislead you
- [[sampling-aliasing]] — Periodic sampling artifacts
- [[skid]] — Interrupt attribution error
- [[mfence-profiling-distortion]] — Fence cost misattribution
- [[long-tail-latency]] — Rare high-latency events
- [[hardware-performance-counters]] — CPU-level counters
- [[gprof-calling-context-lies]] — gprof's unreliable attribution

### Clusters & Cloud Computing (L30)
- [[message-passing-multi-computer]] — Communication across machines
- [[mpi]] — Message Passing Interface
- [[rest-apis-for-distributed-systems]] — HTTP inter-service calls
- [[apache-kafka]] — Distributed streaming platform
- [[sns-and-sqs]] — AWS messaging services
- [[cloud-computing]] — On-demand compute
- [[cloud-instances]] — Virtual machines in the cloud
- [[clusters-vs-laptops]] — When scaling isn't worth it
- [[scalability-cost]] — Overhead of distributed systems

### Queueing Theory (L31-L33)
- [[queueing-theory]] — Mathematical study of waiting lines
- [[queueing-terminology]] — Arrival, service, queue discipline
- [[kendall-notation]] — A/S/k notation for queue types
- [[arrival-rate-and-service-rate]] — Lambda and mu
- [[littles-law]] — L = lambda * W
- [[utilization]] — Server busy fraction (rho)
- [[saturation]] — When utilization approaches 1
- [[mm1-queue]] — Single-server Markov queue
- [[mmk-queue]] — Multi-server Markov queue
- [[open-vs-closed-systems]] — External arrivals vs fixed population
- [[bottleneck-device]] — Limiting resource in a system
- [[visitation-ratio]] — Request routing frequencies
- [[red-line-overload]] — System capacity ceiling
- [[measuring-service-rate]] — Determining mu empirically
- [[performance-modelling-process]] — Steps for building models
- [[one-fast-server-vs-many-slow]] — Pooling vs parallelism tradeoff
- [[task-assignment-policies]] — How to distribute work
- [[load-balancing]] — Distributing work across servers
- [[convergence]] — Steady-state queue behavior
- [[ergodicity]] — Time averages equal ensemble averages
- [[time-average-vs-ensemble-average]] — Two averaging approaches
- [[markov-process]] — Memoryless stochastic process
- [[balking]] — Customers refusing to join long queues
- [[reneging]] — Customers leaving before service
- [[loss-systems]] — Queues that reject when full
- [[priority-queuing]] — Serving by priority class
- [[virtual-queues]] — Logical queue abstraction
- [[multiple-services]] — Queues with multiple service types
- [[service-interchangeability]] — Substitutable servers
- [[maintenance-and-downtime]] — Server unavailability
- [[simulation-for-queueing]] — Monte Carlo queue simulation
- [[fastpass-case-study]] — Disney's queue optimization

### DevOps (L34-L35)
- [[devops]] — Development + Operations culture
- [[continuous-integration]] — Automated build and test
- [[configuration-as-code]] — Version-controlled config
- [[infrastructure-as-code]] — Declarative infrastructure
- [[terraform]] — IaC tool by HashiCorp
- [[common-infrastructure]] — Shared platform components
- [[service-naming]] — Consistent service identification
- [[cattle-not-pets]] — Disposable vs precious servers
- [[containers]] — Lightweight isolated environments
- [[kubernetes]] — Container orchestration
- [[canary-deployment]] — Gradual rollout strategy
- [[rollback]] — Reverting to previous version
- [[monitoring-and-alerting]] — Watching system health
- [[health-checks]] — Automated liveness probes
- [[alert-fatigue]] — Too many alerts cause ignoring
- [[incident-reports]] — Post-incident documentation
- [[root-cause-vs-proximate-cause]] — Deep vs surface cause
- [[five-whys]] — Toyota's root cause technique
- [[security-in-devops]] — Security in operations
- [[supply-chain-attacks]] — Compromised dependencies (xz attack)
- [[vulnerability-management]] — Tracking known CVEs
- [[information-exposure]] — Data leak risks (GDPR)
- [[cryptomining-abuse]] — Hijacking compute for mining
