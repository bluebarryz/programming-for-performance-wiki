---
tags:
  - concept
  - ece459
  - async
lectures:
  - L05
prerequisites:
  - "[[blocking-vs-non-blocking-io]]"
  - "[[callbacks]]"
  - "[[polling-and-event-driven-io]]"
---

# Libcurl Easy and Multi

libcurl is a C library for transferring files, with Rust bindings available. It has two interfaces: the easy (synchronous) interface and the multi (asynchronous) interface.

The **easy** interface uses [[callbacks]]: you create an `Easy` handle, set the URL, provide a write callback via `write_function()`, and call `perform()` which blocks until the transfer is complete. The callback is invoked as data arrives.

The **multi** interface is the key to asynchronous I/O with libcurl. A `Multi` handle holds multiple `Easy2` handles. You add easy handles with `add2()`, then call `perform()` repeatedly -- it returns the number of handles still in progress. When all handles report zero, everything is done. Between `perform()` calls, you call `wait()` to block until something happens. Status is checked via `messages()`. Completed handles are removed with `remove2()`. The developer claims a single multi handle can support up to 60,000 connections.

## Prerequisites
- [[blocking-vs-non-blocking-io]] — The easy interface is blocking; the multi interface is non-blocking
- [[callbacks]] — The easy interface uses callbacks to handle incoming data
- [[polling-and-event-driven-io]] — The multi interface uses a poll-and-perform loop

## Lectures
- [[L05-Asynchronous-IO]]

## Related Concepts
- [[callbacks]]
- [[blocking-vs-non-blocking-io]]
- [[polling-and-event-driven-io]]
