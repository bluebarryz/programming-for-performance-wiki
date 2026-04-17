---
tags:
  - lecture
  - ece459
  - cloud
  - clusters
  - distributed
lecture: 30
title: Clusters & Cloud Computing
date: 2024-09-17
prerequisite_lectures:
  - "[[L01-Programming-for-Performance]]"
  - "[[L05-Asynchronous-IO]]"
---

# L30 - Clusters & Cloud Computing

When a single machine is not enough, you scale to multiple computers. This lecture covers message passing as the required communication model for multi-computer systems (since shared memory is not available across machines). It surveys communication mechanisms: MPI (historical), REST APIs, and Apache Kafka (a distributed streaming platform based on producers, topics with partitions, and consumers). AWS services SNS and SQS are mentioned as alternatives. The cloud computing model (launching/terminating instances, continuous deployment, cloud storage) is described using Amazon EC2 as an example. The lecture closes with the "Scalability! But at what COST?" paper, which shows that 128-core big data systems do not consistently beat a well-written single-threaded laptop implementation for graph processing.

## Prerequisite Lectures
- [[L01-Programming-for-Performance]] — Need scalability concepts before multi-machine scaling
- [[L05-Asynchronous-IO]] — Need async IO patterns for distributed communication models

## Concepts Covered

- [[message-passing-multi-computer]]
- [[mpi]]
- [[rest-apis-for-distributed-systems]]
- [[apache-kafka]]
- [[sns-and-sqs]]
- [[cloud-computing]]
- [[cloud-instances]]
- [[clusters-vs-laptops]]
- [[scalability-cost]]
