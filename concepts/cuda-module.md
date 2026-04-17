---
tags:
  - concept
  - ece459
  - gpu
  - L22
prerequisites:
  - "[[ptx]]"
  - "[[cuda-host-code]]"
---

# CUDA Module

A CUDA module is a package of code and data to run on the device. In practice, you read the compiled [[ptx]] code into a C-String and create the module from it. The module can also be loaded directly from a file.

The module contains the kernel functions that can then be referenced by name in the `launch!` macro. For example, `module.calculate_forces` refers to the `calculate_forces` kernel within the loaded module.

## Prerequisites
- [[ptx]] — A module is created by loading compiled PTX code
- [[cuda-host-code]] — Module loading is part of the host code launch sequence

## Lectures

- [[L22-GPU-Programming-Continued]]

## Related Concepts

- [[ptx]]
- [[cuda-host-code]]
- [[cuda-kernel-launch]]
