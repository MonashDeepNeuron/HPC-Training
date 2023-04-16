# Introduction to Parallel Computing

## What is Parallel Computing?

Parallel computing is about executing the instructions of the program simultaneously

One of the core values of computing is the breaking down of a big problem into smaller easier to solve problems, or at least smaller problems.

In some cases, the steps required to solve the problem can be executed simultaneously (in parallel) rather than sequentially (in order)

A supercomputer is not just about fast processors. It is multiple processors working together in simultaneously. Therefore it makes sense to utilise parallel computing in the HPC environment, given the access to large numbers of processors

![Running Processes in Parallel](imgs/Running%20Processes%20in%20Parallel.png)

An example of parallel computing looks like this. 

![Parallel Computing Example](imgs/Parallel%20Computing%20Example.png)

Here there is an array which contains numbers from 0 to 999. The program is to increment each values by 1. Comparing serial code on left and parallel code on right, parallel code is utilising 4 cores of a CPU. Therefore, it can expect approximately 4 times speed up from just using 1 core, what we are seeing here is how the same code can in-fact execute faster as four times as many elements can be updated in the same time one would be.

## Parallel Computing Memory Architectures

Parallel computing has various memory architectures

### Shared Memory Architecture:

There is shared memory architectures where multiple CPUs runs on the same server. OpenMP uses this model

![Shared Memory Architecture](imgs/Shared%20Memory%20Architecture.png)

### Distributed Memory Architecture:

This distributed memory architecture where CPU and memory are bundled together and works by communicating with other nodes. Message passing protocol called lMPI is used in this model

![Distributed Memory Architecture](imgs/Distributed%20Memory%20Architecture.png)

### Hybrid Parallel Programming:

For High Performance Computing (HPC) applications, OpenMP is combined with MPI. This is often referred to as Hybrid Parallel Programming. 

![Hybrid Parallel Programming](imgs/Hybrid%20Parallel%20Programming.png)