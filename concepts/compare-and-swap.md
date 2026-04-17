---
tags:
  - concept
  - ece459
  - L12
  - concurrency
  - atomics
prerequisites:
  - "[[atomic-operations]]"
---

# Compare-and-Swap

Compare-and-swap (CAS), also called compare-and-exchange, is one of the most important [[atomic-operations]]. It combines a read, comparison, and write into a single uninterruptible operation. On x86 it is implemented by the `cmpxchg` instruction.

Pseudocode:
```c
int compare_and_swap(int* reg, int oldval, int newval) {
    int old_reg_val = *reg;
    if (old_reg_val == oldval)
        *reg = newval;
    return old_reg_val;
}
```

If CAS returns `oldval`, the swap succeeded. Otherwise, another thread changed the value and you should retry (possibly with a delay). Only one thread succeeds when multiple attempt CAS simultaneously.

In Rust: `compare_and_swap(expected, new, ordering)` on atomic types. Also available: `swap` (unconditional), `compare_exchange`, and `compare_exchange_weak`.

CAS is the foundation for [[spinlock]] implementations and [[lock-free-data-structures]], but is susceptible to the [[aba-problem]].

## Prerequisites

- [[atomic-operations]] — CAS is built on top of hardware atomic primitives

## Lectures

- [[L12-Lock-Convoys-Atomics-Lock-Freedom]]

## Related Concepts

- [[atomic-operations]]
- [[spinlock]]
- [[aba-problem]]
- [[lock-free-data-structures]]
