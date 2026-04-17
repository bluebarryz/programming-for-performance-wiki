---
tags:
  - concept
  - ece459
  - pogo
  - optimization
lectures:
  - L27
prerequisites:
  - "[[profile-guided-optimization]]"
  - "[[compiler-optimization-levels]]"
---

# Devirtualization

Devirtualization is the compiler optimization of replacing a virtual (dynamic dispatch) call with a direct (static) call when the concrete type can be determined. In Rust, this applies to trait objects -- if a `&dyn Polite` reference almost always points to a `Kenobi` instance, the compiler can optimize for that case.

Without profiling data, the compiler cannot know which concrete type is most common when multiple types implement a trait. [[profile-guided-optimization|POGO]] collects this information during training runs and uses it for "virtual call speculation" -- optimizing the common case while still handling the uncommon types correctly.

If only one type implements a trait, devirtualization is straightforward. The difficulty arises when multiple types are possible and the compiler needs runtime data to know which is most likely.

## Example

### Virtual call speculation with POGO

```rust
trait Polite { fn greet(&self) -> &str; }

struct Kenobi;
struct Vader;

impl Polite for Kenobi { fn greet(&self) -> &str { "Hello there!" } }
impl Polite for Vader  { fn greet(&self) -> &str { "I am your father." } }

fn print_greeting(p: &dyn Polite) {
    println!("{}", p.greet());
}
```

Without PGO, `p.greet()` is always an indirect vtable call — the CPU must load the function pointer and jump through it, preventing inlining.

After a training run where `Kenobi` accounts for 95% of calls, the compiler transforms the call site into roughly:

```rust
fn print_greeting(p: &dyn Polite) {
    if /* p is Kenobi */ {
        println!("{}", "Hello there!");   // direct call, inlinable
    } else {
        println!("{}", p.greet());        // fallback indirect call
    }
}
```

The hot path becomes a direct (possibly inlined) call with no vtable indirection. The slow path is still correct for `Vader` and any future implementors.

## Prerequisites

- [[profile-guided-optimization]] — POGO provides the runtime type data needed for virtual call speculation
- [[compiler-optimization-levels]] — Devirtualization is a compiler optimization enhanced by profile data

## Lectures

- [[L27-Program-Profiling-and-POGO]]

## Related Concepts

- [[profile-guided-optimization]]
- [[pogo-optimizations]]
