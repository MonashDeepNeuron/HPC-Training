# Challenges

## Challenge 1 - Sum and Product Algorithms

This challenge involves implementing the sum and product reductions on an array or memory block of integers. As a bonus challenge, try and make the algorithms more generic and work with any binary operator.

## Challenge 2 - Array Concatenation

In this challenge you have to implement an array concatenation function. This should join two arrays of the same type into a single array, similar to `strcat()`. You will need to allocate a new block of memory and in order to store the concatenated arrays which will requires the sizes of the two input arrays to be known by the function. This function should return a pointer to the resulting array.

> Note: The type of the array this function concatenates can be any type except `char`.

## Challenge 3 - Doing it in Docker

Pull an Ubuntu image from the Docker registry, install any required dependencies and execute the same C code that you wrote for challenge 2 within that running container instance.

## Challenge 4 - Bash Process Dump

Write and execute a Bash script that captures the process id, process (cmd) name and Nice score and outputs it all into a text file.

## Challenge 5 - Scheduler evaluation

Write a C program that computes the average turnaround time based on these process stats:

| Process | Arrival Time | Burst Time |
|---------|--------------|------------|
|   P1    |      0       |     3      |
|   P2    |      1       |     5      |
|   P3    |      2       |     2      |
|   P4    |      3       |     4      |
|   P5    |      4       |     6      | 