---
tags:
  - concept
  - ece459
  - performance
  - external-services
lectures:
  - L16
prerequisites:
  - "[[rate-limiting]]"
  - "[[caching]]"
---

# Request Grouping

Request grouping (batching) is a strategy for reducing API call count by combining multiple requests into a single larger request. For example, instead of five separate requests to update five employees, use one request that updates all five.

## Considerations

- The remote API must support batch operations
- Can combine related or unrelated requests if the API allows
- Requires buffering requests and deciding how long to wait before sending
- Error handling is more complex: does a single invalid item reject the whole batch or just that item?
- Overlaps with write-back [[caching]] strategies that accumulate modifications before flushing
- The logic for building and interpreting larger requests is more complex and bug-prone

Like most performance techniques in this course, it trades implementation complexity for improved performance. Use it only when needed.

## Prerequisites

- [[rate-limiting]] — Grouping is a strategy specifically for staying under rate limits
- [[caching]] — Write-back caching is a related batching strategy

## Lectures

- [[L16-Rate-Limits]]

## Related Concepts

- [[rate-limiting]]
- [[caching]]
- [[request-throttling]]
