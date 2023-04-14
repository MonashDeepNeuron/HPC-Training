# OpenMPI

OpenMPI is a standard defining message passing between processors in distributed environments.

The MPI (message passing interface) in OpenMPI is a communication protocol standard implemented by different groups and its main goals are high performance, scalability, and portability

OpenMPI is one implementation of the MPI standard. It consists of a set of headers library functions that you call from your program. i.e. C, C++, Fortran etc

For C, you will need a header file for all the functions (mpi.h) and link in the relevant library functions. This is all handled by the mpicc program (or your compiler if you wanted to specify all the paths).
