# Challenges

🚧 Under Construction 🏗️

## Task 1 - Parallise `for` Loop

Goal: To to create an array `[0,1,2...100000]`

1. Git clone [HPC-Training-Challenges](https://github.com/MonashDeepNeuron/HPC-Training-Challenges)
2. Go to the directory `challenges/parallel-computing` and open `array.c` file
3. Implement the code to create an array `[0,1,2...100000]` without parallelisation
4. Measure the run time of the code
5. Use `#pragma<>` and potentially other clauses to parallelise the code
6. Compile the code again and check the run time and observe the result

## Task 2 - Run task 1 on HPC cluster

1. Log into M3
2. Check the available partitions with `show_cluster`
3. Modify `RunHello.sh` to you can run `array.c` on HPC cluster
4. Submit the job to M3
5. Check the slurm output file

>You can also use [strudel web](https://beta.desktop.cvl.org.au/login) to run the script without sbatch

## Task 3 - Reduction Clause

Goal: To find the sum of the array elements

1. Implement the code in `reduction.c` to find the sum of the array elements without parallelisation 
2. Measure the run time of the code
3. Add `#pragma<>` and potentially other clauses to parallelise the code
4. Compile and run `reduction.c` again
5. Check the run time and observe the result 

>`module load gcc` to use newer version of gcc if you have error with something like `-std=c99`

## Task 4 - Private clause

The goal of this task is to square each value in array and find the sum of them

1.  Implement the code in `private.c` to square each value in array and find the sum of them without parallelisation
2. Measure the run time of the code. (You may need to link the math library with `-lm`)
3.  Add `#pragma<>` and potentially other clauses to parallelise the code
4.  Compile `private.c` again and check the run time and observe the result

## Task 5 - Calculate Pi using "Monte Carlo Algorithm"

Goal:  To estimate the value of pi from simulation

1. Implement Monte Carlo in `MonteCarlo.c` without parallelisation
2. Measure the run time of the code
3. Parallelise the code 
4. Compile and run `MonteCarlo.c` again
5. Check the run time and observe the result

> You should get a result close to pi(3.1415…….)

Short explanation of Monte Carlo algorithm:

[YouTube Video:  Monte Carlo Simulation](https://www.youtube.com/watch?v=7ESK5SaP-bc&ab_channel=MarbleScience)

![Monte Carlo](imgs/Monte%20Carlo.png)

## Bonus - Laplace equation to calculate the temperature of a square plane

1. Modify `laplace2d.c` and implement the laplace algorithm
2. Use Makefile to compile the code
3. Make the program as fast as you can

Brief Algorithm of Laplace equation:
![](imgs/Pasted%20image%2020230326142826.png)