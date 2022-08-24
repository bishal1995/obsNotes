Spark EMR Config 
* Spark Settings
	* `maximizeResourceAllocation` : True or False, default : False
		* Settings configured in `spark-defaults` when `maximizeResourceAllocation` is enabled
			* spark.default.parallelism
				* Description : Default number of partitions in RDDs returned by transformations like join, reduceByKey, and parallelize when not set by user.
				* Value : 2X number of CPU cores available to YARN containers.
			* spark.driver.memory
				* Description : Amount of memory to use for the driver process, i.e. where SparkContext is initialized. (for example, 1g, 2g).
				* Value : Setting is configured based on the instance types in the cluster
			* spark.executor.memory
				* Description : Amount of memory to use per executor process.
				* Value : Setting is configured based on the core and task instance types in the cluster.
			* spark.executor.cores
				* Description : The number of cores to use on each executor.
				* Value : Setting is configured based on the core and task instance types in the cluster.
			* spark.executor.instances
				* Description : The number of executors.
				* Value : Setting is configured based on the core and task instance types in the cluster.
	* Spark defaults set by Amazon EMR - No need to configure
		* spark.executor.memory : Setting is configured based on the core and task instance types in the cluster.(Amount of memory to use per executor process. (for example, 1g, 2g))
		* spark.executor.cores :  Setting is configured based on the core and task instance types in the cluster.(number of cores to use on each executor)
		* spark.dynamicAllocation.enabled : true (emr-4.4.0 or greater),Whether to use dynamic resource allocation, which scales the number of executors registered with an application up and down based on the workload.
	* Configuring node decommissioning behaviour : Default value
		*  spark.blacklist.decommissioning.enabled : true
		* spark.blacklist.decommissioning.timeout : 1h
		* spark.decommissioning.timeout.threshold : 20s
		* spark.resourceManager.cleanupExpiredHost : true
		* spark.stage.attempt.ignoreOnDecommissionFetchFailure : true




Following cluster configurations when you work with EMR Studio.
* Livy
	```
	{
	    "classification":"livy-conf",
	        "Properties":{
	            "livy.server.session.timeout":"6h",
	            "livy.spark.deploy-mode":"cluster"
	        }
	}
	```
* Set deploy mode for Spark sessions to cluster mode
* Use memory optimised instances, Eg : r5.2x, r5.4x, r5.8x, r5.12x, r5.16x, r4.2x, r4.4x, r4.8x, r4.12,
* Use the capacity-optimized allocation strategy for Spot Instances to help Amazon EMR make effective instance selections based on real-time capacity insights from Amazon EC2. For more information, see [Allocation strategy for instance fleets](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-instance-fleet.html#emr-instance-fleet-allocation-strategy).
* 