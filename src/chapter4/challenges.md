# Parallel Computing Challenges

## Overview

- [Parallel Computing Challenges](#parallel-computing-challenges)
  - [Overview](#overview)
  - [Pre-Tasks](#pre-tasks)
  - [Task 1 - Single Cluster Job using OpenMP](#task-1---single-cluster-job-using-openmp)
  - [Task 2 - Parallel `for` Loop](#task-2---parallel-for-loop)
  - [Task 3 - Parallel Reductions](#task-3---parallel-reductions)
  - [Task 4 - Laplace Equation for Calculating the Temperature of a Square Plane](#task-4---laplace-equation-for-calculating-the-temperature-of-a-square-plane)
  - [Task 5 - Calculate Pi using "Monte Carlo Algorithm"](#task-5---calculate-pi-using-monte-carlo-algorithm)

## Pre-Tasks

Make sure to clone a copy of **your** challenges repo onto M3, ideally in a personal folder on vf38_scratch.

> Note: For every challenge you will be running the programs as SLURM jobs. This is so we don't overload the login nodes. A template [SLURM job script](./job.slurm) is provided at the root of this directory which you can use to submit your own jobs to SLURM by copying it to each challenges sub-directory and filling in the missing details. You may need more than one for some challenges. This template will put the would-be-printed output in a file named `slurm-<job-name>.out`.

## Task 1 - Single Cluster Job using OpenMP

Create a program in `hello.c` that prints 'Hello, world from thread: <thread-number>' to the output. Launch the job to a node SLURM.

> Note:
>
> - The output of a job is put in a slurm-<job-id>.out file by default.
> - The template slurm job scripts will output the results to a `slurm-<job-name>.out` file.

## Task 2 - Parallel `for` Loop

In `array-gen.c` implement a program that generates an array containing the numbers 0..10'000 elements (inclusive) using a `for` loop. Measure the execution time using the `time` Linux command. Now reimplement the program to utilise OpenMP's parallel `for` loop macros, measuring the execution time again. Is there any performance improvement? Are the elements still in the correct order and if not how can you fix this. Try experimenting with different sized arrays and element types.

> Hint: You will likely need to allocate memory from the heap.

## Task 3 - Parallel Reductions

In the C chapter we created a sum program that summed the elements of an array together. Using this as a base, create a new program that again computes the sum of the elements of an array but using OpenMP, comparing the execution time between the sequential and parallel versions. Is there any performance improvement? How would using a different binary operator change our ability to parallelize the the reduction?

If you have time, implement the sum but at each iteration, raise the current value to the power of the current accumulation divide by 100, adding this to the accumulation. Test a serial and parallel version. Is the parallel any faster?

> Note: `module load gcc` to use newer version of gcc if you have error with something like `-std=c99`.

## Task 4 - Laplace Equation for Calculating the Temperature of a Square Plane

For this challenge you will attempt to parallelize an existing implementation of the Laplace Equation. Throughout the source files of this project there are various loops you can try and make faster by utilizing OpenMP macros. See if you can make a faster version in the `laplace2d-parallel.c`. To build these files make sure you're in that directory and use the command `make`. The executables will be in the same directory.

## Task 5 - Calculate Pi using "Monte Carlo Algorithm"

For this challenge you will have to try and implement the Monte Carlo algorithm with no framework or template and using everything you've learnt so far. Good luck.

[Short explanation of Monte Carlo algorithm](https://www.youtube.com/watch?v=7ESK5SaP-bc&ab_channel=MarbleScience)
