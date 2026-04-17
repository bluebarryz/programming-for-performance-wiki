---
tags:
  - concept
  - ece459
  - gpu
  - L22
prerequisites:
  - "[[gpu-memory-hierarchy]]"
  - "[[cuda-host-code]]"
---

# CUDA Device Buffers

Device buffers are used for moving data to and from the GPU. CUDA requires explicit communication: input data must be put into a buffer and transferred to the device, and output data is transferred back from device buffers to host memory.

In RustaCUDA, `DeviceBuffer::from_slice()` creates a buffer from host data. Each buffer is converted to a device pointer using `as_device_ptr()` when passed to the kernel launch. For scalar types (like `count`), no conversion is needed. After the kernel completes and the stream is synchronized, results are copied back with `copy_to()`.

The `DeviceBuffer::from_slice()` call is itself a memory copy issued on the default stream.

## Prerequisites
- [[gpu-memory-hierarchy]] — Device buffers manage data in the GPU memory hierarchy
- [[cuda-host-code]] — Buffer allocation is part of the host code launch sequence

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[cuda-host-code]]
- [[gpu-memory-hierarchy]]
- [[device-copy-trait]]
- [[rustacuda]]
