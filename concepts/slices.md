---
tags:
  - concept
  - ece459
  - rust
lectures:
  - L03
prerequisites:
  - "[[borrowing-and-references]]"
---

# Slices

A slice is a reference to a contiguous subset of elements in a collection. The most common example is a string slice (`&str`), which refers to a portion of a `String`. Slices are created using range syntax, such as `&s[0..5]`. Internally, a slice stores a pointer to the starting element and a length, without owning the underlying data.

Slices can apply to vectors and other collections, not just strings. As with other references, the existence of a slice prevents modification of the underlying data, which avoids race conditions on collections. Slices also avoid the need to copy data, which matters for performance -- you get a lightweight view into existing data rather than allocating and copying a new collection.

## Prerequisites
- [[borrowing-and-references]] — A slice is a reference to a contiguous subset of a collection

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[borrowing-and-references]]
- [[borrow-checker]]
