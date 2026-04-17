---
tags:
  - concept
  - ece459
  - gpu
  - L22
prerequisites:
  - "[[cuda-host-code]]"
---

# CUDA Stream

A CUDA stream is where you issue commands such as memory copies, kernel launches, etc. Commands on the same stream execute in order, while commands on different streams may execute out of order.

Commands that do not specify a stream are issued on the *default stream*. The stream is asynchronous: once a command is issued, it returns immediately. You must call `stream.synchronize()` to wait for all commands in the stream to complete before reading results. The `DEFAULT` flag is used to issue the kernel launch on the default stream so it executes after memory copies issued on that same stream.

## Prerequisites
- [[cuda-host-code]] — Streams are created and used within the host code launch sequence

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-host-code]]
- [[cuda-kernel-launch]]
- [[rustacuda]]
