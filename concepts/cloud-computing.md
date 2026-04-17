---
tags:
  - concept
  - ece459
  - distributed-systems
lectures:
  - "30"
prerequisites:
  - "[[scalability]]"
  - "[[parallelism]]"
---

# Cloud Computing

Cloud computing enables on-demand provisioning of compute resources, allowing you to spin up dozens or thousands of server instances when you need more capacity, and shut them down when you don't. This evolved from dedicated physical servers, to virtualized slices of physical machines, to the elastic cloud model exemplified by Amazon's Elastic Compute Cloud (EC2).

In cloud computing, you pay according to the number and size of instances you run. Providers offer different instance sizes varying in cores, local storage, memory, and sometimes GPUs. Launching an instance involves selecting a virtual machine image, after which the instance gets an IP address and full root access. When an instance is no longer needed, terminating it stops all charges and destroys its local data. Persistent data must be stored separately using cloud storage (e.g., Amazon S3), block storage (e.g., EBS), or cloud databases.

The ability to launch and terminate instances also enables continuous deployment: new instances with updated software can be started before old ones are shut down, avoiding downtime. However, care must be taken with incompatible changes such as database schema migrations. Cloud computing makes clusters accessible without large upfront hardware investment, but the overhead of distributed systems means that scaling to many machines is not always faster than a well-optimized single-machine solution.

## Prerequisites

- [[scalability]] — Cloud computing is motivated by the need to scale beyond a single machine
- [[parallelism]] — Cloud instances run workloads in parallel across multiple machines

## Lectures
- [[L30-Clusters-Cloud-Computing]]

## Related Concepts
- [[cloud-instances]]
- [[clusters-vs-laptops]]
- [[scalability-cost]]
- [[scalability]]
