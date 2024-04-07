# Parallel & Distributed Computing

Nearly all modern computer systems utilise parallel computing to speed up the execution of algorithms. To see how this works in practice look at the diagram below.

![parallel vs. distributed](imgs/parallel-distributed.png)

As you can see, in a scenario where a program (job) takes 3 seconds and 3 independent jobs have to be executed by a system, doing it serially in a single computer takes a total of 9 seconds. But doing it simultaneously across 3 computers will only take 3 seconds thus achieving a 3x speedup through parallel computing. 

This is the fundamental principle that High Performance Computing is based on.

## What is Distributed Computing? 

**Distributed computing is parallel execution on distributed memory architecture.**

This essentially means it is a form of parallel computing, where the processing power is spread across multiple machines in a network rather than being contained within a single system. In this memory architecture, the problems are broken down into smaller parts, and each machine is assigned to work on a specific part.

![distributed memory architecture](imgs/distributed_memory_architecture.png)

### Distributed Memory Architecture

Lets have a look at the distributed memory architecture in more details.

- Each processor has its own local memory, with its own address space
- Data is shared via a communications network using a network protocol, e.g Transmission Control Protocol (TCP), Infiniband etc..

![Distributed Memory Architecture](imgs/distributed_memory_architecture_2.png)

Each machine or **node** is connected to the HPC cluster via a network, typically one with high bandwidth and low latency. The fact that these are largely independent computers connected over a network rather than a set of CPU/GPU cores in the same computer (in parallel computing), presents a set of disadvantages.

__Advantages of parallel & local computing:__
- No **data transfer latency** & I/O throughput bottleneck. The system bus inside a machine has incredibly higher bandwidth and lower latency compared to even the fastest computer networks.
- 