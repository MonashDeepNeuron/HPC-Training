# Job Batching

## spark-submit

The spark-submit script found in Spark's bin directory serves to initiate applications on a cluster. It seamlessly integrates with all of Spark's supported cluster managers via a unified interface, eliminating the need for specific configuration adjustments tailored to each one individually.

```bash
# Remember to change the master_node to actual master node's name
source /path/to/spark-3.5.0-bin-hadoop3/bin/spark-submit \
    --master spark:{master_node}:7077 \ 
    hello_world.py
```

> Here is a comprehensive [documentation](https://spark.apache.org/docs/3.5.0/submitting-applications.html#launching-applications-with-spark-submit) of all `spark-submit` options. We will not look into the detail of it (If you need to find any command, it should be better to look directly into the documentation itself). Instead, we will focus on M3 and see how we can bundle and submit everything as Slurm jobs.

## Slurm and Spark

Here is a complete bash script that we can `sbatch` to M3. We will now go through what is happening here:

```bash
#!/bin/bash
#SBATCH --job-name=SparkSlurm
#SBATCH --nodes=4
#SBATCH --time=00:15:00
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=4096
#SBATCH --cpus-per-task=1
#SBATCH --partition=m3i

############################ Spark Cluster #######################################

# This is basically the same steps as seen in the first subchapter

# Remember to change this to the actual path
export SPARK_HOME="/path/to/spark-3.5.0-bin-hadoop3"

# Add to the global PATH
export PATH="${SPARK_HOME}/bin:${PATH}"

 # Get all worker nodes and write to the config file of Spark
scontrol show hostnames | sed -n '2,$p' > $SPARK_HOME/conf/workers

# Start the spark cluster
$SPARK_HOME/sbin/start-all.sh

################################### Submit Job ###################################

# Get the master node, which will be the first node from the command `scontrol show hostnames`
master_node=$(scontrol show hostnames | head -1)

# Submit job to the Spark Cluster using spark-submit
# In this script we submit a provided example in the spark directory
$SPARK_HOME/bin/spark-submit \
    --master spark://${master_node}:7077 \
    $SPARK_HOME/examples/src/main/python/pi.py \
    1000
```
