# Message Passing

As each processor has its own local memory with its own address space in distributed computing, we need a way to communicate between the processes and share data. Message passing is the mechanism of exchanging data across processes. Each process can communicate with one or more other processes by sending messages over a network.

The MPI (message passing interface) in OpenMPI is a communication protocol standard defining message passing between processors in distributed environments and are implemented by different groups with the main goals being high performance, scalability, and portability.

OpenMPI is one implementation of the MPI standard. It consists of a set of headers library functions that you call from your program. i.e. C, C++, Fortran etc.

For C, you will need a header file for all the functions (mpi.h) and link in the relevant library functions. This is all handled by the mpicc program (or your compiler if you wanted to specify all the paths).

In the next chapter we will look at how to implement message passing using OpenMPI.
