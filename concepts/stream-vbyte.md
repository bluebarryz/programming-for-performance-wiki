---
tags:
  - concept
  - ece459
  - performance
  - simd
  - encoding
lectures:
  - L17
prerequisites:
  - "[[simd]]"
  - "[[vbyte-encoding]]"
  - "[[inverted-indexes]]"
  - "[[branch-prediction]]"
---

# Stream VByte

Stream VByte is a [[simd]]-accelerated variant of [[vbyte-encoding]] for decoding variable-length integers, particularly useful in [[inverted-indexes]].

## How It Works

Stream VByte separates the data into two streams: a **control stream** and a **data stream**. The control stream uses 2 bits per integer to encode its size (00 = 1 byte, 01 = 2 bytes, 10 = 3 bytes, 11 = 4 bytes). Each control byte thus describes 4 integers, using all 8 bits as data.

Each decode iteration:
1. Reads a byte from the control stream
2. Reads 16 bytes from the data stream
3. Uses a lookup table to determine how many of those 16 bytes are needed
4. Uses the SIMD "shuffle" instruction (`_mm_shuffle_epi8`) to rearrange the bytes into proper integer positions in a 128-bit register

The shuffle mask is precomputed and read from an array at execution time.

## Why It's Fast

- Control bytes are sequential, so the processor can always prefetch the next one (predictable location)
- Data bytes are sequential, loaded at high throughput
- The shuffle instruction takes 1 cycle
- Control flow is regular -- no conditional jumps, just a tight loop of load/shuffle/store

## Core Implementation (C++)

```c
uint8_t C = lengthTable[control];
__m128i Data = _mm_loadu_si128((__m128i *) databytes);
__m128i Shuf = _mm_loadu_si128(shuffleTable[control]);
Data = _mm_shuffle_epi8(Data, Shuf);
databytes += C; control++;
```

## Prerequisites

- [[simd]] — Stream VByte uses SIMD shuffle instructions for branchless decoding
- [[vbyte-encoding]] — Stream VByte is a SIMD-optimized variant of VByte encoding
- [[inverted-indexes]] — The primary use case motivating Stream VByte
- [[branch-prediction]] — Understanding why branch mispredictions in naive VByte decoders are costly

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[simd]]
- [[vbyte-encoding]]
- [[inverted-indexes]]
