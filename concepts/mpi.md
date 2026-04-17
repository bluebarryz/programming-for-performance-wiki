---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[message-passing-multi-computer]]"
---

# MPI

MPI (Message Passing Interface) is a de facto standard for programming message-passing multi-computer systems, historically prominent in high-performance computing (HPC). It provides a standardized API for sending and receiving messages between processes running on different machines, supporting both point-to-point and collective communication patterns.

While MPI sounds good in principle, in practice it has fallen out of favor for many use cases. People tend to use other communication mechanisms such as [[rest-apis-for-distributed-systems]], [[apache-kafka]], or cloud-native messaging services like [[sns-and-sqs]]. The decline of MPI's relevance is discussed in detail in Jonathan Dursi's "HPC is dying, and MPI is killing it" (2015), which argues that MPI's rigid programming model and the overhead of its ecosystem have become liabilities.

Despite its declining popularity, MPI remains relevant as a conceptual touchstone for understanding message-passing patterns in multi-computer systems, and it still sees use in scientific computing and other traditional HPC domains where its communication primitives align well with the problem structure.

## Prerequisites

- [[message-passing-multi-computer]] — MPI is a specific standard for multi-computer message passing

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[message-passing-multi-computer]]
- [[apache-kafka]]
- [[rest-apis-for-distributed-systems]]
