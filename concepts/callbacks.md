---
tags:
  - concept
  - ece459
  - async
lectures:
  - L05
prerequisites:
  - "[[closures-and-capturing]]"
---

# Callbacks

A callback is a function (often a closure) passed to an API to be invoked when a particular event occurs, such as data arriving from the network. In the [[libcurl-easy-and-multi]] easy interface, you provide a callback via `write_function()` that gets called each time data is received. The callback processes the data (e.g., writes it to stdout) and returns the number of bytes handled.

In the multi interface, `messages()` takes an `FnMut` callback to check the status of completed requests. Callbacks are a fundamental building block of asynchronous programming -- they let you define what should happen when an operation completes, without blocking the thread. However, deeply nested callbacks can be hard to reason about, which is one motivation for the [[futures-and-async-await]] model.

## Prerequisites
- [[closures-and-capturing]] — Callbacks in Rust are typically implemented as closures

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[libcurl-easy-and-multi]]
- [[closures-and-capturing]]
- [[futures-and-async-await]]
