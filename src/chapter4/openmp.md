# Parallel Computing with OpenMP

## What is OpenMP

OpenMP, stand for open multi-processing is an API for writing multithreaded applications

It has a set of compiler directives and library routines for parallel applications, and it greatly simplifies writing multi-threaded code in Fortran, C and C++.

Just few lines of additional code can make your application parallel 

OpenMP uses shared memory architecture. It assumes all code runs on a single server

## Threads

![Threads Visualisation](imgs/Threads%20Visualisation.png)

A thread of execution is the smallest instruction that can be managed independently by an operating system.

In parallel region, multiple threads are spawned and utilises the cores on CPU

> Only one thread exists in a serial region

## Compiler Directive \# pragma

-   Source codes with “#” provide additional information to compiler
-   `#define X 10`
-   `#include <omp.h>`
-   `#pragma omp parallel`
  
OpenMP provides a set of `#pragma` directives that can be used to specify the parallelization of a particular loop or section of code. For example, the `#pragma omp parallel` directive is used to start a parallel region, where multiple threads can execute the code concurrently. The `#pragma omp for` directive is used to parallelize a loop, with each iteration of the loop being executed by a different thread.

Here's an example of how `#pragma` directives can be used with OpenMP to parallelize a simple loop:
  
  
Use `gcc -fopenmp` to compile your code when you use `#pragma`

## Compile OpenMP

1. Add `#include <omp.h> if you are using OpenMP function`
2. Run `gcc -fopenmp -o hello hello.c`

## How it works

![OpenMP and Directive](imgs/OpenMP%20and%20Directive.png)
[Source](https://www.researchgate.net/figure/OpenMP-API-The-master-thread-is-indicated-with-T-0-while-inside-the-parallel-region_fig3_329536624 
)

Here is an example of `#pragma`
- The function starts with serial region
- At the line `#pragma omp parallel`, a group of threads are spawned to create parallel region inside the bracket 
- At the end of the bracket, the program goes back to serial computing 

## Running "Hello World" on Multi-threads

>If you're unsure about the difference between **multi-threading** and **multi-processing**, check the page [here](multithreading.md)

**Drawing in Serial (Left) vs Parallel (Right)**
![](imgs/4%20Parallel%20Computing%20OpenMP.gif)

Drawing in serial versus drawing in parallel, you can see how we can place one pixel at a time and take a long time to make the drawing, but on the right hand side if we choose to load and place four pixels down simultaneously we can get the picture faster, however during the execution it can be hard to make out what the final image will be, given we don’t know what pixel will be placed where in each execution step.

Now this is obviously a fairly abstract analogy compared to exactly what’s happening under the hood, however if we go back to the slide diagram containing zones of multiple threads and serial zones, some parts of a program must be serial as if this program went further and drew a happy face and then a frown face, drawing both at the same time is not useful to the program, yes it would be drawn faster but the final image won’t make sense or achieve the goal of the program.

## How many threads? You can dynamically change it

**`omp_set_num_threads()` Library Function**
Value is set inside program. Need to recompile program to change

**`OMP_NUM_THREADS` Environment Variable**

```bash
export OMP_NUM_THREADS=4 
./hello
```

The operating system maps the threads to available hardware. You would not normally want to exceed the number of cores/processors available to you.

## Measuring Performance

The command `top` or `htop` looks into a process. As you can see from the image on right, it shows the CPU usages.

![Top Command](imgs/Top%20Command.png)

The command `time` checks the overall performance of the code.

![Time Command](imgs/Time%20Command.png)

By running this command, you get real time, user time and system time.

**Real** is wall clock time - time from start to finish of the call. This includes the time of overhead

**User** is the amount of CPU time spent outside the kernel within the process

**Sys** is the amount of CPU time spent in the kernel within the process. 
**User** time + **Sys** time will tell you how much actual CPU time your process used. 

## More Features of OpenMP

- [YouTube Video: Introduction to OpenMP](https://www.youtube.com/watch?v=iPb6OLhDEmM&list=PLLX-Q6B8xqZ8n8bwjGdzBJ25X2utwnoEG&index=11 )
- [YouTube Video: Data environment -\#pragma omp parallel private](https://www.youtube.com/watch?v=dlrbD0mMMcQ&list=PLLX-Q6B8xqZ8n8bwjGdzBJ25X2utwnoEG&index=17)
- [YouTube Video: Parallel Loops - \#omp parallel for reduction()](https://www.youtube.com/watch?v=iPb6OLhDEmM&list=PLLX-Q6B8xqZ8n8bwjGdzBJ25X2utwnoEG&index=11 )