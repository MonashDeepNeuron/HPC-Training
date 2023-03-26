# Challenges

## Task 1 - Parallise for Loop

Goal: To to create an array [0,1,2………...19]

1. Git clone https://github.com/Yusuke710/HPC_training2021.git 
2. Go to the directory “question”. Compile array.c and execute it. Check the run time of the serial code
3. Add `#pragma<>` 
4. Compile the code again
5. Run parallel code and check the improved run time

## Task 2 - Run task 1 on HPC cluster

1.  Check the available partitions with `show_cluster`
2.  Modify `RunHello.sh `
3.  `sbatch RunHello.sh`
4.  `cat slurm<>.out` and check the run time

>[!note]
>You can also use strudel web to run the script without sbatch: https://beta.desktop.cvl.org.au/login  

## Task 3 - Reduction Clause

Goal: To find the sum of the array elements

1.  Compile `reduction.c` and execute it. Check the run time
2.  Add `#pragma<>`
3.  Compile `reduction.c` again
4.  Run parallel code and check the improved run time. Make sure you got the same result as the serial code

>[!note]
>`module load gcc` to use newer version of gcc if you have error with something like `-std=c99`

## Task 4 - Private clause

The goal of this task is to square each value in array and find the sum of them
1.  Compile private.c and execute it. Check the run time. `#include` the default library `<math.h>` and link it
2.  Add `#pragma<>`
3.  Compile `private.c` again
4.  Run parallel code and check the improved run time

## Task 5 - Calculate Pi using "Monte Carlo Algorithm"

Goal:  To estimate the value of pi from simulation

-   No instructions on this task. Use what you have learnt in previous tasks to run a parallel code!
-   You should get a result close to pi(3.1415…….)

Short explanation of Monte Carlo algorithm:

[https://www.youtube.com/watch?v=7ESK5SaP-bc&ab_channel=MarbleScience](https://www.youtube.com/watch?v=7ESK5SaP-bc&ab_channel=MarbleScience)

![](src/chapter4/_attachments/Pasted%20image%2020230326142805.png)

## Bonus - Laplace equation to calculate the temperature of a square plane

- Modify `laplace2d.c`
- Use Makefile to compile the code
- Make the program as fast as you can

Brief Algorithm of Laplace equation:
![](src/chapter4/_attachments/Pasted%20image%2020230326142826.png)