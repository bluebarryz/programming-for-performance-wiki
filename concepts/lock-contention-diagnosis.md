---
tags:
  - concept
  - ece459
  - locks
  - diagnostics
lectures:
  - L26
prerequisites:
  - "[[bottleneck-analysis]]"
  - "[[locking-and-synchronization]]"
---

# Lock Contention Diagnosis

If CPU usage is unexpectedly low and this is not explained by I/O waits, lock contention may be the cause. In this situation, many threads will be blocked waiting for locks.

There is no standard `locktrace` tool for user-space locks, and POSIX pthreads does not include lock tracing. Possible approaches:

- **Manual logging/tracing**: record when a thread wants to enter, enters, and leaves a critical section
- **`perf lock`**: only finds kernel-space lock contention, not user-space
- **Helgrind** (Valgrind suite): detects lock ordering problems that cause deadlock (a correctness issue rather than a performance issue)
- **Commercial tools** like Intel VTune claim to detect user-space lock contention

Deadlock is considered a correctness problem rather than a performance problem in this course.

## Prerequisites

- [[bottleneck-analysis]] — Lock contention diagnosis is one step in systematic bottleneck analysis
- [[locking-and-synchronization]] — Understanding locks and their purpose is required to diagnose contention

## Lectures

- [[L26-Finding-Bottleneck-Devices]]

## Related Concepts

- [[bottleneck-analysis]]
- [[cpu-profiling]]
