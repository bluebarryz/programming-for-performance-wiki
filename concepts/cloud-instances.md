---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[cloud-computing]]"
---

# Cloud Instances

A cloud instance is a virtual machine running in a cloud provider's data center. Instances are launched from a virtual machine image, receive an IP address, and provide full root access. Providers like Amazon EC2 offer a variety of instance sizes that differ in number of cores, local storage, memory, and optionally GPUs.

The lifecycle of a cloud instance has three key phases. Launching provisions the instance from an image that can contain any pre-configured software stack, including tools like Hadoop or OpenMPI. While running, the instance behaves like a normal server accessible over the network. Terminating the instance stops all charges, but also destroys all local data, making it essential to persist important results to external storage such as cloud block storage, databases, or object stores like Amazon S3.

This ephemeral nature enables continuous deployment workflows: new instances running updated software are launched before old ones are terminated, providing zero-downtime updates. The pay-per-use model means you only pay for the compute time you actually consume, which is particularly valuable for bursty workloads that need large compute capacity only intermittently.

## Prerequisites

- [[cloud-computing]] — Cloud instances are the fundamental unit of cloud computing

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[cloud-computing]]
- [[scalability-cost]]
- [[clusters-vs-laptops]]
