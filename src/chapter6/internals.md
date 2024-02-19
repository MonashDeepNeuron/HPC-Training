# Spark Architecture Overview

Here is a diagram representing components of Apache Spark:

![Architecture](./imgs/spark-architecture.png)

## Cluster Managers

Spark is designed to smoothly scale from just one compute node to potentially thousands. It achieves this scalability while prioritizing flexibility by supporting various cluster managers, including Hadoop YARN, Apache Mesos, and its own Standalone Scheduler. For our setup, we've opted for the simplicity of the Standalone Scheduler to run a mini-cluster in the last section.

## Spark Core - Resillient Distributed Datasets (RDDs)

### What is RDDs?

An RDD is simply a immutable distributed collection of objects. Within Spark, all tasks involve either generating new RDDs, modifying existing ones, or executing operations on RDDs to produce an outcome. Behind the scenes, Spark seamlessly disperses the data stored within RDDs into multiple partitions across your cluster and parallelizes the tasks you execute on them. Moreover, RDD can accommodate Python, Java, or Scala objects of any type, including user-defined classes. RDDs enable users to explicitly persist intermediate outcomes in memory, control their partitioning to optimize data distribution, and manipulate them using a diverse set of operators.

### Initialize RDD

#### Parallelize Collections

We can create a RDD from an existing iterable or collection

```python
data: list = ["H", "e", "l", "l", "o", "!"]

# by default, set the number of partitions automatically based on your cluster
chars: RDD = spark_context.parallelize(data)

# you can also set it manually by passing it as a second parameter to parallelize
chars: RDD = spark_context.parallelize(data, 10)
```

#### Read from External Datasets

PySpark can create distributed datasets from any storage source supported by Hadoop, including your local file system, HDFS, Cassandra, HBase, Amazon S3,...

```python
# takes a URI for the file (either a local path on the machine, or a hdfs://, s3a://, etc URI)
# reads it as a collection of lines
lines: RDD = spark_context.textFile("/path/to/hello.txt")
```

Once created, RDD can be performed on by a diverse list of functional-style operations.

### RDD Operations

RDDs support two types of operations `transformations` and `actions`: 
- Transformations are operations on RDDs that return a new RDD by applying the same operation to many data items. Transformations are `lazily evaluated` (including loading data), it will only be computed when an action is called. Spark internally records metadata to indicate that a transformation has been requested.
- Actions are operations that run computation on a RDD then return a value (non-RDD) or export data to a storage system.

#### Transformations

| Name         | Description |
| ------------ | ----------- |
| map          |             |
| filter       |             |
| flatMap      |             |
| sample       |             |
| groupByKey   |             |
| reduceByKey  |             |
| union        |             |
| join         |             |
| cogroup      |             |
| crossProduct |             |
| mapValues    |             |
| sort         |             |
| partitionBy  |             |

#### Actions

| Name    | Description                     |
| ------- | ------------------------------- |
| count   |                                 |
| collect |                                 |
| reduce  |                                 |
| lookup  |                                 |
| save    | Outputs RDD to a storage system |

#### Examples

TODO

### Data Partitioning

TODO
