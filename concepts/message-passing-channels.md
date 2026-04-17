---
tags:
  - concept
  - ece459
  - rust
  - concurrency
lectures:
  - L03
prerequisites:
  - "[[ownership]]"
  - "[[rust-threads]]"
---

# Message Passing (Channels)

Message passing in Rust uses channels from `std::sync::mpsc` (multiple-producer, single-consumer). A channel has a transmit end (`tx`) where messages are submitted and a receive end (`rx`) where messages arrive. The ownership mechanic works like postal mail: when you send a value, you relinquish ownership of it, and the receiver takes ownership.

The `recv()` call is blocking -- the receiving thread waits until a message arrives. There is also a non-blocking `try_recv()`. To have multiple sending threads, you clone the transmitter and hand clones to each thread. The type being sent must implement the [[send-trait]]. Message passing is generally safer than shared memory because it is harder to race or access inappropriate locations -- the structure enforces that data flows in one direction.

## Prerequisites
- [[ownership]] — Sending a message transfers ownership to the receiver
- [[rust-threads]] — Channels communicate between threads

## Lectures
- [[L03-Rust-Borrowing-Slices-Threads-Traits]]

## Related Concepts
- [[rust-threads]]
- [[fearless-concurrency]]
- [[send-trait]]
- [[mutex]]
