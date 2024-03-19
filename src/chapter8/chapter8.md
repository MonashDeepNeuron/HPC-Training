# Parallel and Distributed Computing

In this chapter, we will discuss the abstraction of parallel computing and distributed computing. To facilitate our exploration, we will employ two sets of APIs within the C Programming Language: OpenMP and OpenMPI. These tools will serve as a means to concretely illustrate the underlying language-independent theory.

## Parallel Computing

**Parallel computing is about executing the instructions of the program simultaneously.**

One of the core values of computing is the breaking down of a big problem into smaller easier to solve problems, or at least smaller problems. In some cases, the steps required to solve the problem can be executed simultaneously (in parallel) rather than sequentially (in order).

## Distributed Computing

**Distributed computing is parallel execution on distributed memory architecture.**

This essentially means it is a form of parallel computing, where the processing power is spread across multiple machines in a network rather than being contained within a single system. In this memory architecture, the problems are broken down into smaller parts, and each machine is assigned to work on a specific part.