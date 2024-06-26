# Apache Spark Challenges

## Overview

- [Apache Spark Challenges](#apache-spark-challenges)
  - [Overview](#overview)
  - [Task 1 - Classic Distributed Problem: Token Counting](#task-1---classic-distributed-problem-token-counting)
  - [Task 2 - Cluster Set-up Bash Scripts](#task-2---cluster-set-up-bash-scripts)
  - [Task 3 - Spark and Slurm](#task-3---spark-and-slurm)
  - [Task 4 - Data Processing](#task-4---data-processing)
  - [Task 5 - Spark Machine Learning](#task-5---spark-machine-learning)

> Note: Tasks 1, 2, and 3 closely resemble a **typical workflow** when working with Apache Spark:
> - **Step 1**: Interactively work with a small sample of the problem
> - **Step 2**: Solve and optimize the sample problem
> - **Step 3**: Submit the entire larger problem as a batch job
> - **Step 4**: Analyze the result and, if necessary, repeat steps 1 to 4
> 
> You should employ this workflow into task 4 and task 5

## Task 1 - Classic Distributed Problem: Token Counting

Given a string of tokens, count the number of times each token apprears. You should do this task in an interactive JupyterLab notebook connecting to a Spark cluster. This is a cananical problem of distributed data processing, and often served as an example for [MapReduce Programming Model](https://en.wikipedia.org/wiki/MapReduce).

> Hint: Have a look at [map()](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.RDD.map.html) and [reduceByKey()](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.RDD.reduceByKey.html)

## Task 2 - Cluster Set-up Bash Scripts

Write Bash Scripts to streamline the process of installing Spark and running the cluster.
> Hint: Try to combine the [subchapter: set up](./set-up.md)

## Task 3 - Spark and Slurm

Submit [task 1](#task-1---calculate-pi-using-monte-carlo-algorithm-again) as a Spark job using Slurm. This should be similar to [subchapter: job batching](./job-batching.md)
> Hint:
> - You will need to convert the notebook into a Python file.
> - Compare the content of `$SPARK_HOME/examples/src/main/python/pi.py` and [our Monte Carlo Pi Estimation](./internals.md#monte-carlo-pi-estimation). They both solve the same problem, however, there are stuffs that we don't need to add when directly using `spark-submit`. Why?

## Task 4 - Data Processing

In this task, we will start working witha dataframe and try to process a given real-world dataset.

> The dataset, at around ~100MB, is considered small and not well-suited for Spark utilization (opting for Pandas might be more efficient). Nevertheless, working with this dataset serves as an exercise to understand more about Spark concepts and its capabilities.

## Task 5 - Spark Machine Learning

We will use the data from task 4 to build an intro-to-Machine-Learning model, [Linear Regression](https://en.wikipedia.org/wiki/Linear_regression), with [MLlib](https://spark.apache.org/mllib/)
