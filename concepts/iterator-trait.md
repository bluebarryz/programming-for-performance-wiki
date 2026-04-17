---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[traits]]"
---

# Iterator Trait

The `Iterator` trait in Rust is placed on a collection to allow iterating over it. It is often more efficient than a typical `for` loop with index-based access, because it lets the compiler skip bounds checking and apply other optimizations. Underestimating the overhead of array indexing compared to using an iterator is listed as one of the common [[rust-pitfalls]] in the course.

Iterators are lazy in Rust -- they do not compute values until consumed. They compose well with closures for operations like `map`, `filter`, and `fold`, enabling expressive and performant data processing chains without intermediate allocations.

## Prerequisites
- [[traits]] — Iterator is a trait; understanding the trait system is needed

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[traits]]
- [[rust-pitfalls]]
