# Linux Commands

Even if you are already familiar with linux, please read through all of these commands, as some are specific to M3.

## Basic Linux Commands

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

> Note: `.` and `..` are special directories. `.` is the current directory, and `..` is the parent directory. These can be used when using any command that takes a directory as an argument. Similar to these, `~` is the home directory, and `$` is the root directory. For example, if you wanted to copy something from the parent directory to the home directory, you could do `cp ../<filename> ~/`, without having to navigate anywhere.

## Cluster Specific Commands

| Command | Function | Flags
| --- | --- | --- |
| `show_job` | prints information about your jobs |
| `show_cluster` | prints information about the cluster |
| `user_info` | prints information about your account |
| `squeue` | prints information about your jobs | `-u <username>` to print information about a specific user |
| `sbatch <slurm_script_file>` | submit a job to the cluster |
| `scontrol show job <JOBID>` | prints information about a specific job |
| `scancel <JOBID>` | cancel a job |

## M3 Specific Commands

| Command | Function |
| --- | --- |
| `module load <module_name>` | load a module |
| `module unload <module_name>` | unload a module |
| `module avail` | list available modules |
| `module list` | list loaded modules |
| `module spider <module_name>` | search for a module |
| `module help <module_name>` | get help for a module |
| `module show <module_name>` | show details about a module |
| `module purge` | unload all modules |
| `module swap <module_name> <module_name>` | swap two modules |