# Apache Spark

Apache Spark is an open-source, distributed computing system that has gained immense popularity for its speed, ease of use, and versatility in handling large-scale data processing tasks. Developed to overcome the limitations of the MapReduce paradigm, Spark offers a unified platform for various data processing workloads, including batch processing, real-time data streaming, machine learning, and graph processing.

Spark provides high-level APIs in languages like Scala, Java, Python, and R, making it accessible to a wide range of developers with different programming backgrounds.

In this chapter, we will:
- Set up a mini Spark cluster in M3. 
- Take a closer look at the internal data structure, specifically Resilient Distributed Datasets (RDDs). 
- Explore data processing in Spark and JupyterLab.
- Submit batch jobs utilizing both Slurm and Spark
- Engage in some challenges.

> Notes:
> - The material covered in this chapter draws heavily from the [official documentation of Spark 3.5.0](https://spark.apache.org/docs/latest/index.html).
> - [Setting up a Spark Cluster within M3 via Slurm](./set-up.md#setting-up-a-spark-cluster-within-m3-cluster) and [Submit Spark Job inside Slurm Job](./job-batching.md#job-batching) both involve a trial-and-error approach, as it doesn't adhere to any official documentation. Consequently, there's a likelihood that it may not be the best practice. Thus, if you've discovered alternative methods or more effective approaches or may be even security vulnerabilities, please don't hesitate to submit a pull request.
