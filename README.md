# til

Roadsigns along the way (normally found after hours of strife)

* 21-12-17: Docker for Mac default binds to 'no particular address' `0.0.0.0`, not to loopback `127.0.0.1`
* 22-01-18: PySpark might need `spark.executorEnv.PYTHONHASHSEED` set to a random int, as 3.3+/Spark 2+ doesn't seem to set this on the executors
* 25-01-18: If in client mode, PySpark will need to have `spark.driver.memory` set in init vs. at runtime (e.g. `spark-submit --driver-memory 10G`)
* 02-02-18: `s3(n/a)` filesystem support ships with Hadoop2.4, 2.5+ require additional `hadoop-aws` dependency
* 12-02-18: Keras (especially when booting on a fresh EC2 instance) will often need the env variables 
```
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64"
export CUDA_HOME=/usr/local/cuda
```