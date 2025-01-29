Topic to prepare
- Computation Model (Mop Reduce)
-  Execution Model
	- Tranformations
		-   Narrow : Operations where each input partition contributes to exactly one output partition
			-  Map
			-  Filter
			-  Union
		-  Wide : Operations where each input partition contributes to multiple output partitions
			-  GroupByKey
			-  ReduceByKey
			-  Join
	- Actions
		-  Reduce
		-  Count
		-  Collect
		-  First
		-  Take
		-  ForEach
-  Optimisations
	- Code Optimization
	- Configuration tuning
		- Resource tuning
			-  Memory 
				- Executor Memory
				- Driver Memory
				- Memory fraction
			- 
	-  Data Structure
		- DataFrame
		- RDD ( Immutable )
		- Datasets
	- Algorithm
		- Proper algo for distributed computation
	- Common performance bottleneck
		- Data shuffling : Shuffle is the process of redistributing data across partitions during certain operations like groupBy or join where data needs to be rearranged. Excessive shuffling can impact performance negatively by introducing network overhead, disk I/O, and increased computational complexity.
		- Data Skew : Uneven data partition --- Problem
			- Partitioning : Proper partitioning is crucial for efficient parallel processing and minimizing data movement during transformations.
				- Different partitioning schemes
					- Hash : Hash function is applied to each record based on a specific key. Useful when you need to group data by a specific key
					- Range : Splits data into ordered ranges. Each partition contains a specified range of data based on a column value. Effective when dealing with sorted or ordered data, such as time-series data. 
					- Range based : Round robin partitioning evenly distributes records across partitions without any key-based partitioning. Useful for creating balanced partitions when no specific key is required, such as in parallel processing where record order does not matter. (Shuffling data or using random keys.)
					- Broadca
			- Sampling : Identify skewed keys or values using sampling techniques and apply data skew mitigation strategies like replication or redistribution.
			- Custom partitioner :  Implement custom partitioners to handle skewed data distribution more efficiently.Example needed
			- Salting : Adding a random prefix to keys to distribute skewed data evenly across partitions.
		- Inefficient joins : Optimising Joins
			-  Choosing Join types : Broadcast join for one of the smaller tables and hash joins for bigger tables
			-  Ensuring joined datasets are properly partitioned on the join key.
			-  Join predicate should filter data before joining and reduce size before joining
			-  Broadcasting small tables to all executors to avoid unnecessary data shuffling
		- Resource Contention
		- Serialization Overhead
		-  Caching(in memory) and persistence(flexible caching) : To cache/persist frequently accessed 
	-  Monitor and debug performance issues in PySpark
		- Spark UI : Monitor resource utilization
		- Logging : Enable detailed logging
		-  Profiling : Using Sparklens
-   **Architecture** -- Find better content
	- ![[0_w5OgGQ0xC9zVoULQ.webp]]
	- Driver Program
	- Cluster Manager
	- Worker Nodes
	- Executors
-  SparkContext Vs SparkSession
-  Spark deployment mode
	-  Local Mode : All spark components like driver, executor runs in the same JVM
	-  Client Mode : 
	-  Cluster mode : 
-  **Streaming**
	-   Spark Streaming : Works on micro batching,  DStream / Discretized(Powered by RDD) stream. A continious stream of data, We can apply transformations and actions on it.
	-  Structured Streaming : Built on Dataframe and Dataser API, can be used with sparkSQL API.
		- Differences
			- RDD Vs DataStream/Dataset
			- Processing with event time, handling late data
				- There is no concept of event time in Spark Streaming, it is present int structured streaming





































































