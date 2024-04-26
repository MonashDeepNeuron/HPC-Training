# M3 Challenges

## Challenge 1

Navigate to your scratch directory and, using vim (or your chosen in-terminal editor) create a file called `hello.txt` that contains the text "Hello World". Once you have created the file, use the `cat` command to print the contents of the file to the screen.

## Challenge 2

Write a bash script that prints the contents of the above hello.txt file to the screen and run it locally (on your login node).

## Challenge 3

Submit the above script to the queue by writing another SLURM bash script. Check the status of the job using `squeue`. Once the job has finished, check the output using `cat`. You can find the output file in the directory you submitted the job from.

## Challenge 4

Request an interactive node and attach to it. Once you have done this, install python 3.7 using conda.

## Challenge 5

Clone and run [this](./dl_on_m3/alexnet_stl10.py) script. You will need to first install the dependencies for it. You don't need to wait for it to finish, just make sure it is working. You will know its working if it starts listing out the loss and accuracy for each epoch. You can stop it by pressing `ctrl + c`.

Once you have confirmed that it is working, deactivate and delete the conda environment, and then end the interactive session.

> Hint: I have included the dependencies and their versions (make sure you install the right version) in the `requirements.txt` file. You will need python 3.7 to run this script.

## Challenge 6

Go back to the login node. Now you are going to put it all together. Write a bash script that does the following:

- (1) requests a compute node
- (2) installs python using conda
- (3) clones and runs the above script

Let this run fully. Check the output of the script to make sure it ran correctly. Does it match the output of the script you ran in challenge 5?
> Hint: You can check the output of the script at any time by `cat`ing the output file. The script does not need to have finished running for you to do this.

## Challenge 7

Edit your submission script so that you get a gpu node, and run the script using the gpu.
> Hint: Use the m3g partition

## Challenge 8

Now you want to clean up your working directory. First, push your solutions to your challenges repo. Then, delete the challenges directory, as well as the conda environment you created in challenge 6.
