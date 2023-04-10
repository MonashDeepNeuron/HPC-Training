# Job batching & SLURM

Launching and running jobs on M3 is controlled by [SLURM](https://slurm.schedmd.com/). You don't really need to know a lot about it in order to use it, so this section will take you through the basics of what you will need for what we are doing.

If you want a complete guide on SLURM in M3, you can find it [here](https://docs.massive.org.au/M3/slurm/slurm-overview.html).

## Submitting simple jobs

As we discussed in the previous section we use bash scripts to run jobs on M3. We can submit these jobs using the `sbatch` command. For example, if we have a bash script called `hello.sh` that contains the following:

```bash
#!/bin/bash

#SBATCH --ntasks=1
#SBATCH --mem=1MB
#SBATCH --time=0-00:01:00
#SBATCH --job-name=hello
#SBATCH --partition=m3i
#SBATCH --mail-user=jmar0066@student.monash.edu
#SBATCH --mail-type=BEGIN,END,FAIL

echo "Hello World"
```

We can submit this job using the following command:

`sbatch hello.sh`

This will submit the job to the queue, and you will get an email when the job starts, finishes, or fails. You can also check the status of your job using the `squeue` command.

## Options

You might have noticed the `#SBATCH` lines in the bash script. These are called options, and they tell SLURM how to run the job. The options we used in the example above are:

- `ntasks`: The number of tasks or processes to run.
- `mem`: The amount of memory to allocate to the job.
- `time`: The maximum amount of time the job can run for.
- `job-name`: The name of the job. Up to 15 characters.
- `partition`: The partition to run the job on.
- `mail-user`: The email address to send job status emails to.
- `mail-type`: The types of emails to send.

There are a lot more options that you can use, and you can find a more complete list [here](https://docs.massive.org.au/M3/slurm/simple-batch-jobs.html).

In particular, if you want to run multithreading or multiprocessing jobs, or you need a gpu, there are more options you need to configure.

## Interactive jobs

Sometimes you might want to actually connect to the node that you are running your job on, in order to see what is happening or to set it up before running the job. You can do this using the `smux` command. Similar to regular batch jobs, you can set options when you start the interactive session. An example of this is:

`smux new-session --ntasks=1 --time=0-00:01:00 --partition=m3i --mem=4GB`

This will start an interactive session on a node with 1 cpu, 1 minute of time, and 4GB of memory. There are again other options available, and you can find a more complete explanation [here](https://docs.massive.org.au/M3/slurm/interactive-jobs.html).

### Connecting to interactive jobs

Typically when you start an interactive job it will not start immediately. Instead, it will be queued up once it has started you will need to connect to it. You can do this by running `smux a`, which will reconnect you to the session. If you want to disconnect from the session but leave it running, you can press `Ctrl + b` followed by `d`. This will disconnect you from the session, but leave it running. You can reconnect to it later using `smux a`. If you want to kill the session, if you are connected just run `exit`, otherwise if you are in a login node run `scancel <jobid>`. You can find the job id using `show_job`.

## Checking the status of jobs, finding out job IDs, and killing jobs

A couple of useful commands for general housekeeping are:

- `squeue`: This will show you the status of all jobs currently running on M3.
- `show_job`: This will show you the status of all jobs you have submitted.
- `squeue -u <username>`: This will show you the status of all jobs submitted by a particular user currently running.
- `scancel <jobid>`: This will kill a job with a particular job id.
- `scancel -u <username>`: This will kill all jobs submitted by a particular user.
- `show_cluster`: This will show you the status of the cluster, including any nodes that are offline or in maintenance.
