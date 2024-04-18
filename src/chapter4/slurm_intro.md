# SLURM

Slurm (Simple Linux Utility for Resource Management) is an open-source workload manager/scheduler for the M3 MASSIVE cluster. It was created back in the mid-2000s by SchedMd and now it's used by approximately 65% of the world's supercomputers. Slurm is basically the intermediary between the Login node and compute nodes. Hence, the Slurm scheduler is the gateway for the users on the login node to submit work/jobs to the compute nodes for processing.

Slurm has three key functions. 
1. It provides exclusive and/or non-exclusive access to the resources on the compute nodes to the users for a certain amount of time. Hence, the users can perform any computation with the resources. 
2. It provides a framework to start, execute, and check the work on the set of allocated compute nodes. 
3. It manages the queue of pending jobs based on the availability of resources.

## Basic Linux Commands

Since Slurm and M3 nodes are implemented on Linux, it's necessary to know some basic Linux commands. You will have to be comfortable using these commands, writing Bash scripts and navigating the Linux environment in order to be successful in a lot of our HPC projects.

| Command | Function |
| --- | --- |
| `pwd` | prints current directory |
| `ls` | prints list of files / directories in current directory (add a `-a` to list everything, including hidden files/directories |
| `mkdir` | makes a directory |
| `rm <filename>` | deletes *filename*. add `-r` to delete directory. add `-f` to force deletion (be really careful with that one) |
| `cd <directory>` | move directory.  |
| `vim` or `nano` | bring up a text editor |
| `cat <filename>` | prints contents of file to terminal |
| `echo` | prints whatever you put after it |
| `chmod <filename>` | changes permissions of file |
| `cp` | copy a file or directory|
| `mv <filename>` | move or rename file or directory |

> Note: `.` and `..` are special directories. `.` is the current directory, and `..` is the parent directory. These can be used when using any command that takes a directory as an argument. Similar to these, `~` is the home directory, and `/` is the root directory. For example, if you wanted to copy something from the parent directory to the home directory, you could do `cp ../<filename> ~/`, without having to navigate anywhere.

## Bash Scripts

Bash is both a command line interface and a scripting language. Linux commands are generally using Bash. Bash scripts are a series of commands that are executed in order. Bash scripts are useful for automating tasks that you do often, or for running a series of commands that you don't want to type out every time. In our case, Bash scripts are used for running jobs on M3.

In terms of use, Bash can encapsulate any command you would normally run in the terminal into a script that can be easily reused. For example you could have a script that automatically navigates to a directory and activates a virtual environment, or a script that compiles and runs a C program.

The basic syntax of a bash file is as follows:

```bash
#!/bin/bash

# This is a comment

echo "Hello World"
```

We can save this file as `hello.sh` and run it using the following command: `source hello.sh`. This will print `Hello World` to the terminal.

Let's walk through the file. The first line is `#!/bin/bash`. This is called a shebang, and it tells the system that this file is a bash script. The second line is a comment, and is ignored by the system. The third line is the actual command that we want to run. In this case, we are using the `echo` command to print `Hello World` to the terminal.

Bash can do a lot more, including basic arithmetic, if statements, loops, and functions, however these are not really necesary for what we are doing. If you want to learn more about bash, you can find a good tutorial [here](https://linuxconfig.org/bash-scripting-tutorial).

For our use, the main things we need to be able to do are to run executables and files. We do this the exact same way as if manually running them in the terminal. For example, if we want to run a python script, we can do the following:

```bash
#!/bin/bash

# This will run hello.py using the python3 executable
python3 hello.py
```

If we want to compile and then run a C program, we can do the following:

```bash
#!/bin/bash

# This will compile hello.c and then run it
gcc hello.c -o hello
./hello
```

Using bash scripts not only saves a lot of time and effort, but it also makes it easier to run jobs on M3 using SLURM. We will go over how to do this in the next section.

## Slurm Architecture
Slurm has a centralized manager, slurmctld, to monitor resources and work. Each compute server (node) has a slurmd daemon, which can be compared to a remote shell: it waits for work, executes that work, returns status, and waits for more work. There is an optional slurmdbd (Slurm DataBase Daemon) which can be used to record job accounting information in a database.

![slurm-arch](./imgs/slurm-arch.gif)

## Basic Slurm Commands
Slurm provides a variety of tools for users to submit and manage jobs along with viewing info about them. These commands can be used interactively (on a terminal) in the login node.

| Commands | Syntax | Description |
| --- | --- | --- |
| `sinfo` | `sinfo` | Get information about the resources on available nodes that make up the HPC cluster. |
| `sbatch` | `sbatch <job-id>` | Submit a batch script to Slurm for processing. |
| `srun` | `srun <resource-parameters>` | Run jobs interactively on the cluster. |
| `skill/scancel` | `scancel <job-id>` | End or cancel a queued job. |
| `squeue` | `squeue -u` | Show information about your job(s) in the queue. The command when run without the -u flag, shows a list of your job(s) and all other jobs in the queue. |
| `sacct` | `sacct` | Show information about current and previous jobs.  |

## Slurm Job Scripting
Slurm job scripts are very similar to bash scripts but you will have to use a set of Slurm-specific directives (flags beginnig #) and Slurm-specific & Bash commands. 

In creating a Slurm script, there are **4 main parts** that are mandatory in order for your job to be successfully processed.

1. **Shebang:** The Shebang command tells the shell (which interprets the UNIX commands) to interpret and run the Slurm script using the bash (Bourne-again shell) shell.

> This line should always be added at the very top of your SBATCH/Slurm script. (Same as all Bash scripts)

2. **Resource Request:** In this section, the amount of resources required for the job to run on the compute nodes are specified. This informs Slurm about the name of the job, output filename, amount of RAM, Nos. of CPUs, nodes, tasks, time, and other parameters to be used for processing the job.

> These SBATCH commands are also know as SBATCH directives and must be preceded with a pound sign and should be in an uppercase format as shown below.

```
#SBATCH --job-name=TestJob
#SBATCH --output=TestJob.out
#SBATCH --time=1-00:10:00
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --mem-per-cpu=500M
```

3. **Dependencies:** Load all the software that the project depends on to execute. For example, if you are working on a python project, you’d definitely require the python software or module to interpret and run your code. Go to Chapter 5.6 for more info on this.

```
module load python
```

4. **Job Steps** Specify the list of tasks to be carried out.

```
srun echo "Start process"
srun hostname
srun sleep 30
srun echo "End process"
```

### Putting it all together
Please note that the lines with the double pound signs (##) are comments when used in batch scripts.

```
## Shebang
#!/bin/bash

## Resource Request
#SBATCH --job-name=TestJob
#SBATCH --output=TestJob.out
#SBATCH --time=1-00:10:00
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --mem-per-cpu=500M

## Job Steps
srun echo "`Start process`"
srun hostname
srun sleep 30
srun echo "`End process`"
```

In the script above, 1 Node with 1 CPU, 500MB of memory per CPU, 10 minutes of Walltime was requested for the tasks (Job steps). Note that all the job steps that begin with the srun command will execute sequentially as one task by one CPU only.

The first job step will run the Linux echo command and output Start process. The next job step(2) will echo the Hostname of the compute node that executed the job. Then, the next job step will execute the Linux sleep command for 30 seconds. The final job step will just echo out End process. Note that these job steps executed sequentially and not in parallel.

It’s important to set a limit on the total run time of the job allocation, this helps the Slurm manager to handle prioritization and queuing efficiently. The above example is a very simple script which takes less than a second. Hence, it’s important to specify the run time limit so that Slurm doesn’t see the job as one that requires a lot of time to execute.