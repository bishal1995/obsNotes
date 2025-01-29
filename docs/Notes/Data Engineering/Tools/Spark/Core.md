-> [Map reduce](https://static.googleusercontent.com/media/research.google.com/en//archive/mapreduce-osdi04.pdf)  - Programming model and associated implementation of processing of large datasets


![[Screenshot from 2024-05-07 22-44-51.png]]
The Map invocations are distributed across multiple machines by automatically partitioning the input data into a set of M splits. The input splits can be processed in parallel by different machines. Reduce invocations are distributed by partitioning the intermediate key space into R pieces using a partitioning function.
-> Steps
- The MapReduce library in the user program first splits the input files into M pieces of typically 16 megabytes to 64 megabytes (MB) per piece.  It then starts up many copies of the program on a cluster of machines. One of the copies of the program is special – the master. The rest are workers that are assigned work by the master.
- A worker who is assigned a map task reads the contents of the corresponding input split. It parses key/value pairs out of the input data and passes each pair to the user-defined Map function. The intermediate key/value pairs produced by the Map function are buffered in memory.
- Periodically, the buffered pairs are written to local disk, partitioned into R regions by the partitioning function.The locations of these buffered pairs on the local disk are passed back to the master, who is responsible for forwarding these locations to the reduce workers.
- When a reduce worker is notified by the master about these locations, it uses remote procedure calls to read the buffered data from the local disks of the map workers. When a reduce worker has read all intermediate data, it sorts it by the intermediate keys so that all occurrences of the same key are grouped together. The sorting is needed because typically many different keys map to the same reduce task. If the amount of intermediate data is too large to fit in memory, an external sort is used.
- The reduce worker iterates over the sorted intermediate data and for each unique intermediate key encountered, it passes the key and the corresponding set of intermediate values to the user’s Reduce function. The output of the Reduce function is appended to a final output file for this reduce partition
- When all map tasks and reduce tasks have been completed, the master wakes up the user program. At this point, the MapReduce call in the user program returns back to the user code.

-> Master Data Structure : For each mapReduce task following data are stores
- State( idle, in-progress, completed )
- Identity of worker machine
- Map Tasks : Location and size of R intermediate file region produced by map task, these are send back to reduce workers

->  Fault tolerance
- Worker failure - The master pings every worker periodically. If no response is received from a worker in a certain amount of time, the master marks the worker as failed. All the task in them are set to idle state and becomes eligible for scheduling. 
- Master Failure - Periodic checkpoints are written of the master data structure, On master failure a new master can start from last checkpointed state.
- 
