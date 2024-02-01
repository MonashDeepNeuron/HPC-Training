# Apache Spark Challenges

## Overview

- [Apache Spark Challenges](#apache-spark-challenges)
  - [Overview](#overview)
  - [Task 1 - Calculate Pi using "Monte Carlo Algorithm" (AGAIN!!!)](#task-1---calculate-pi-using-monte-carlo-algorithm-again)
  - [Task 2 - Cluster Set-up Bash Scripts](#task-2---cluster-set-up-bash-scripts)
  - [Task 3 - Spark and SLURM](#task-3---spark-and-slurm)
  - [Task 4 - Data Processing](#task-4---data-processing)
  - [Task 5 - Spark Machine Learning](#task-5---spark-machine-learning)

> Note: Tasks 1 to 3 closely resemble a **typical workflow** when working with Apache Spark:
> - **Step 1**: Interactively work with a small sample of the problem
> - **Step 2**: After solving and optimizing the sample problem, submit the entire larger problem as a batch job
> - **Step 3**: Analyze the result and, if necessary, repeat steps 1 to 3
> 
> You should employ this workflow into task 4 and task 5

## Task 1 - Calculate Pi using "Monte Carlo Algorithm" (AGAIN!!!)

Reimplement Monte Carlo algorithm utilising Spark. You should do this task in an interactive JupyterLab notebook connecting to a Spark cluster.

## Task 2 - Cluster Set-up Bash Scripts

Write Bash Scripts to streamline the process of installing Spark and running the cluster.

## Task 3 - Spark and SLURM

Submit [task 1](#task-1---calculate-pi-using-monte-carlo-algorithm-again) (you will need to convert the notebook into a Python file) as a Spark job using SLURM. This may include wrapping the following steps into 1 single SLURM script:
- Set-up a Spark Cluster
- Submit the job to the cluster using `spark-submit`

## Task 4 - Data Processing

TODO: Find some simple data about 300MB

## Task 5 - Spark Machine Learning

We will use the data from task 4 to build a simple Machine Learning model with [MLlib](https://spark.apache.org/mllib/)