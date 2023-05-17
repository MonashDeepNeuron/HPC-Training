# Distributed Computing Challenges

## Overview

- [Distributed Computing Challenges](#distributed-computing-challenges)
  - [Overview](#overview)
  - [Pre-Tasks](#pre-tasks)
  - [Task 1 - Multinode 'Hello, world!'](#task-1---multinode-hello-world)
  - [Task 2 - Ping Pong](#task-2---ping-pong)
  - [Task 3 - Multinode Sum](#task-3---multinode-sum)
  - [Task 4 - Multinode Mergesort](#task-4---multinode-mergesort)

## Pre-Tasks

For each task you will need to load MPICH using Spack from within your SLURM job script. There is a shared installation of Spack and MPICH within `vf38_scratch`. To load Spack and MPICH use the following to commands within you SLURM job script before any other command.

```sh
. ~/vf38_scratch/spack/share/spack/setup-env.sh
spack load mpich
```

A template SLURM job file is given at the root of the distributed challenges directory. Copy this for each challenge into their respective sub-directories as every challenge will require running a SLURM job. If want to do some more experimenting, create multiple job scripts that use different amounts of nodes and test the execution time.

You will also need to generate some input for the sum and mergesort challenges. This can be done by compiling and running the program in `generate.cpp`. Run the following commands to build an generate the inputs for your challenges.

```sh
module load gcc/10.2.0
g++ -std=c++20 -o bin/generate generate.cpp
bin/generate 1000000000
```

> Note:
>
> - You do not have to worry about how to read the numbers from the file, this is handled for you already but it is recommended to look at the read function in `read.h` and understand what it is doing.
> - The expected output of the 'sum' challenge is found in the generated `output.txt` file within the challenges directory.
> The expected output of the 'mergesort' challenge is found in the generated `sorted.txt` file within the challenges directory however this will contain a lot of values so a check function is provided that compares a resorted version of your input to your sorted output.

## Task 1 - Multinode 'Hello, world!'

Your first task is to say 'Hello, world!' from different nodes on M3. This involves printing the nodes name, rank (ID) and the total number of nodes in the MPI environment.

## Task 2 - Ping Pong

For this next task you will play a Ping-Pong game of sorts between two nodes. This will involve passing a count between the two nodes and incrementing the count for each send and receive. This should increment the count to 10 in the end.

## Task 3 - Multinode Sum

Your next task is to sum the numbers in the generated `input.txt` file together across ten nodes. This will involve summing 1,000,000,000 floats together. The rough expected output is contained in the `output.txt` file. Remember the input array is already given in the template file.

## Task 4 - Multinode Mergesort

Your final task is to sort the numbers from the input file `unsorted.txt` using a distributed version of mergesort. This will involve ten nodes running their won mergesorts on chunks of the input data individually and then a final mergesort of the intermediate results. Remember the input array is already given in the template file.
