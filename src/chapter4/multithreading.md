# Multithreading on HPC

## Thread vs Process

![Thread vs Processes](imgs/Thread%20vs%20Processes.png)

When computer runs a program, your source code is loaded into RAM and process is started.
A **process** is a collection of code, memory, data and other resources.
A process runs in a unique address space. So Two processes can not see each other’s memory. 

A **thread** is a sequence of code that is executed inside the scope of the **process**. You can (usually) have multiple **threads** executing concurrently within the same process. 
**Threads**  can view the memory (i.e. variables) of other threads within the same process

A **multiprocessing** system has more than two processors, whereas **multithreading** is a program execution technique that allows a single process to have multiple code segments. 

## Architecture of a HPC Cluster (Massive)

![Slurm Architecture](imgs/Slurm%20Architecture.png)

The key in HPC is to write a parallel computing code that utilise multiple nodes at the same time. essentially, more computers faster your application

## Using Massive

### Find Available Partition

Command: 
```bash
show_cluster
```

![show_cluster Command](imgs/show_cluster%20Command.png)

Before you run your job, it’s important to check the available resources.

`show_cluster` is a good command to check the available resources such as CPU and Memory. Make sure to also check the status of the of the node, so that your jobs get started without waiting

### Sending Jobs

Command: 
```bash
#SBATCH`--flag=value
```

![sbatch Command](imgs/sbatch%20Command.png)

Here is the example of shell script for running multi-threading job
`#sbatch` specifies resources and then it runs the executable named hello.

`#sbatch` tasks specifies how many processes to run 
Cpus per task is pretty self explanatory, it specifies how many cpu cores you need to run a process, this will be the number of threads used in the job
And make sure to specify which partition you are using

### Monitor Jobs

Command: 
```bash
squeue
# or
squeue -u <username>
```

![squeue Command](imgs/squeue%20Command.png)

After you submitted your job, you can use the command squeue to monitor your job 
you can see the status of your job to check whether it’s pending or running and also how long has it been since the job has started. 