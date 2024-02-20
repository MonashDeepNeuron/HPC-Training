# Job Batching

## spark-submit

The spark-submit script found in Spark's bin directory serves to initiate applications on a cluster. It seamlessly integrates with all of Spark's supported cluster managers via a unified interface, eliminating the need for specific configuration adjustments tailored to each one individually.

```bash
source /path/to/spark-3.5.0-bin-hadoop3/bin/spark-submit \
    --master spark:{master_node}:7077 \
    hello_world.py
```

> Here is a comprehensive [documentation](https://spark.apache.org/docs/3.5.0/submitting-applications.html#launching-applications-with-spark-submit) of all `spark-submit` options. We will not look into the detail of it (If you need to find any command, it should be better to look directly into the documentation itself). Instead, we will focus on M3 and see how we can bundle and submit everything as Slurm jobs.

## Slurm and Spark

TODO