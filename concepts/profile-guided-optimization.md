---
tags:
  - concept
  - ece459
  - optimization
  - pogo
  - compiler
lectures:
  - L27
prerequisites:
  - "[[compiler-optimization-levels]]"
  - "[[cpu-profiling]]"
  - "[[inlining]]"
---

# Profile-Guided Optimization (POGO)

Profile-Guided Optimization (POGO, also called PGO) uses data from actual program runs to inform compiler optimization decisions, overcoming the limitations of static analysis alone. The compiler normally guesses about things like branch likelihood, but these guesses can be wrong. POGO replaces guesses with measured data.

The process has three steps:

1. **Instrument**: compile with `-Cprofile-generate=/tmp/pgo-data` to insert probes that record runtime behavior
2. **Train**: run the instrumented binary with realistic workloads to collect `.profraw` files, then merge them with `llvm-profdata merge`
3. **Recompile**: compile again with `-Cprofile-use=./merged.profdata` to apply the training data

The training phase should use realistic workloads, not exhaustive testing. Exercising every feature is counterproductive -- it teaches the compiler that nothing is important.

Old training data can be reused until the codebase has diverged significantly. The recommended workflow is for one developer to generate the training data and check it into source control.

In benchmarks (Spec2K), POGO achieved speed gains of 6.6% to 36.9% depending on the application.

## Examples

### [[devirtualization]]
See associated page

### Branch layout: hot path gets the fall-through

```c
if (error_condition) {   // rarely true
    handle_error();
} else {
    do_work();           // almost always taken
}
```

Without PGO, the compiler doesn't know which branch is hot. With PGO, it knows `error_condition` is rarely true and lays out `do_work()` as the fall-through — no jump instruction on the common path, better instruction cache utilization.

### Inlining decisions

```rust
fn parse_line(s: &str) -> Record { ... }  // called 10M times in training

fn log_debug(msg: &str) { ... }           // called 3 times in training
```

Static analysis sees both as "called functions." PGO sees that `parse_line` is on the hot path and inlines it aggressively; `log_debug` is cold and left as a call. Without training data, the compiler might inline `log_debug` (small function) and not `parse_line` (larger function).

### Training workload matters

A web server trained only on health-check endpoints (`GET /ping`) will tell the compiler that JSON parsing and auth logic are cold. The resulting binary is fast for health checks but slow for real traffic. Training data must reflect the actual workload distribution.

### Workflow (Rust)

```bash
# Step 1: instrument
RUSTFLAGS="-Cprofile-generate=/tmp/pgo-data" cargo build --release

# Step 2: train with realistic input
./target/release/myapp < realistic_workload.txt

# Step 3: merge profiles
llvm-profdata merge -output=merged.profdata /tmp/pgo-data/*.profraw

# Step 4: recompile with profile data
RUSTFLAGS="-Cprofile-use=./merged.profdata" cargo build --release
```

## Prerequisites

- [[compiler-optimization-levels]] — POGO builds on standard compiler optimizations by adding runtime data
- [[cpu-profiling]] — POGO uses profiling data to guide compiler decisions
- [[inlining]] — Inlining is the primary optimization POGO improves

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[pogo-probes]]
- [[pogo-training]]
- [[pogo-optimizations]]
- [[hot-and-cold-code]]
- [[call-graph-path-profiling]]
