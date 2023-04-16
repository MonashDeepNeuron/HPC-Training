# Challenges

## Challenge 1

Something simple to start off. Create a bash script called `hello.sh` that prints "Hello World" to the screen. Submit this job to the queue using `sbatch`. Check the status of the job using `squeue`. Once the job has finished, check the output using `cat`. You can find the output file in the directory you submitted the job from.

## Challenge 2

Something a bit more involved. Clone your [challenges repository](https://github.com/MonashDeepNeuron/HPC-Training-Challenges.git) into your personal folder in the scratch directory. Then, in this same directory, create a submission script that will install python 3.10 using miniconda, create a virtual environment, install the necessary dependencies, and clone and run the `alexnet_stl10.py` script in the M3 section. Remember, don't directly load python using module, follow the instructions in the [software tooling](./software-tooling.md#python) chapter.
Once completed, commit and push your changes as well as the output.

## Challenge 3

A continuation of challenge 2. Edit your submission script so that you get a gpu node, and run the script using the gpu.
Commit and push your changes as well as the output.
