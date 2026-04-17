---
tags:
  - concept
  - ece459
  - data-structures
  - performance
lectures:
  - L17
prerequisites: []
---

# Inverted Indexes

An inverted index maps terms to lists of document IDs that contain them. For example, given documents {1: "dog, cat, cow", 2: "cat", 3: "dog, goat", 4: "cow, cat, goat"}, the inverted index maps "dog" -> [1, 3], "cat" -> [1, 2, 4], etc.

Inverted indexes support fast lookups by term and boolean queries that combine terms. They contain many small integers (the doc IDs), and since the lists are sorted, it is sufficient to store deltas between consecutive IDs, which are typically small.

This makes inverted indexes a natural use case for [[vbyte-encoding]] and [[stream-vbyte]], which efficiently store and decode sequences of small variable-length integers.

## Prerequisites

None — foundational concept.

## Lectures

- [[L17-Mostly-Data-Parallelism]]

## Related Concepts

- [[vbyte-encoding]]
- [[stream-vbyte]]
- [[simd]]
