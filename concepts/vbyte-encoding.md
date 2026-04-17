---
tags:
  - concept
  - ece459
  - performance
  - encoding
lectures:
  - L17
prerequisites:
  - "[[inverted-indexes]]"
  - "[[branch-prediction]]"
---

# VByte Encoding

VByte is a variable-byte encoding scheme for integers that uses fewer bytes for smaller values. On 64-bit processors, storing small integers in fixed 8-byte words wastes space. VByte uses a control bit (the high-order bit of each byte) to indicate whether more bytes follow:

- `0xxxxxxx`: final byte (values 0 to 127)
- `1xxxxxxx/0xxxxxxx`: two bytes (values 128 to 16383)
- `1xxxxxxx/1xxxxxxx/0xxxxxxx`: three bytes (up to 2^21 - 1)
- etc.

## Performance Trade-offs

VByte saves space by fitting more information into limited RAM and cache, improving throughput. However, a naive decoder has lots of branch mispredictions due to the variable control flow. [[stream-vbyte]] addresses this by using [[simd]] instructions to decode without branches.

## Prerequisites

- [[inverted-indexes]] — VByte encoding is motivated by the need to store many small integers in inverted indexes
- [[branch-prediction]] — Naive VByte decoding suffers from branch mispredictions due to variable control flow

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[stream-vbyte]]
- [[inverted-indexes]]
- [[simd]]
