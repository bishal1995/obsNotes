* #### What is Hudi ?
	* What it provides
		* Table abstraction on data lake
		* Transaction 
		* Efficient upserts.deletes
		* Advanced Indexes
		* Streaming Ingestion
		* Data compaction/clustering 
		* Concurrency
		* 

#### Concepts
* Timeline
	* At its core, Hudi maintains a `timeline` of all actions performed on the table at different `instants`, A Hudi instant consists of the following components
		*   `Instant action` : Type of action performed on the table
		-   `Instant time` : Instant time is typically a timestamp (e.g: 20190117010349), which monotonically increases in the order of action's begin time.
		-   `state` : current state of the instant
	- Hudi guarantees that the actions performed on the timeline are atomic & timeline consistent based on the instant time,Key action performed include
		-   `COMMITS` - A commit denotes an **atomic write** of a batch of records into a table.
		-   `CLEANS` - Background activity that gets rid of older versions of files in the table, that are no longer needed.
		-   `DELTA_COMMIT` - A delta commit refers to an **atomic write** of a batch of records into a MergeOnRead type table, where some/all of the data could be just written to delta logs.
		-   `COMPACTION` - Background activity to reconcile differential data structures within Hudi e.g: moving updates from row based log files to columnar formats. Internally, compaction manifests as a special commit on the timeline
		-   `ROLLBACK` - Indicates that a commit/delta commit was unsuccessful & rolled back, removing any partial files produced during such a write
		-   `SAVEPOINT` - Marks certain file groups as "saved", such that cleaner will not delete them. It helps restore the table to a point on the timeline, in case of disaster/data recovery scenarios.
	- Any given instant can be in one of the following states
		-   `REQUESTED` - Denotes an action has been scheduled, but has not initiated
		-   `INFLIGHT` - Denotes that the action is currently being performed
		-   `COMPLETED` - Denotes completion of an action on the timeline
-  Table & Query Types : Hudi table types define how data is indexed & laid out on the DFS and how the above primitives and timeline activities are implemented on top of such organization (i.e how data is written). In turn, `query types` define how the underlying data is exposed to the queries (i.e how data is read).
	- Table type
		- COW (Copy on write) : File slices in Copy-On-Write table only contain the base/columnar file and each commit produces new versions of base files. In other words, we implicitly compact on every commit, such that only columnar data exists. As a result, the write amplification (number of bytes written for 1 byte of incoming data) is much higher, where read amplification is zero. This is a much desired property for analytical workloads, which is predominantly read-heavy.As data gets written, updates to existing file groups produce a new slice for that file group stamped with the commit instant time, while inserts allocate a new file group and write its first slice for that file group.
		- ![[hudi_cow-9750b5f006646e2d1874ad18b355d200.png]]
		- MOR (Merge On Read) : Stores data using a combination of columnar (e.g parquet) + row based (e.g avro) file formats. Updates are logged to delta files & later compacted to produce new versions of columnar files synchronously or asynchronously .Merge on read table is a superset of copy on write, in the sense it still supports read optimized queries of the table by exposing only the base/columnar files in latest file slices. Additionally, it stores incoming upserts for each file group, onto a row based delta log, to support snapshot queries by applying the delta log, onto the latest version of each file id on-the-fly during query time. Thus, this table type attempts to balance read and write amplification intelligently, to provide near real-time data. The most significant change here, would be to the compactor, which now carefully chooses which delta log files need to be compacted onto their columnar base file, to keep the query performance in check (larger delta log files would incur longer merge times with merge data on query side)
		- ![[hudi_mor-5f9da4e0c57c9ee20b74b31c035ba0e6.png]]
	- Query Type
		- **Snapshot Queries** : Queries see the latest snapshot of the table as of a given commit or compaction action. In case of merge on read table, it exposes near-real time data(few mins) by merging the base and delta files of the latest file slice on-the-fly. For copy on write table, it provides a drop-in replacement for existing parquet tables, while providing upsert/delete and other write side features.
		- **Incremental Queries** : Queries only see new data written to the table, since a given commit/compaction. This effectively provides change streams to enable incremental data pipelines.
		- **Read Optimized Queries** : Queries see the latest snapshot of table as of a given commit/compaction action. Exposes only the base/columnar files in latest file slices and guarantees the same columnar query performance compared to a non-hudi columnar table.
- Indexing : Hudi provides efficient upserts, by mapping a given hoodie key (record key + partition path) consistently to a file id, via an indexing mechanism. This mapping between record key and file group/file id, never changes once the first version of a record has been written to a file. In short, the mapped file group contains all versions of a group of records.
	- Index types
		- **Bloom Index (default):** Employs bloom filters built out of the record keys, optionally also pruning candidate files using record key ranges.
		- **Simple Index:** Performs a lean join of the incoming update/delete records against keys extracted from the table on storage.
		- **HBase Index:** Manages the index mapping in an external Apache HBase table.
		- **Bring your own implementation:** You can extend this [public API](https://github.com/apache/hudi/blob/master/hudi-client/hudi-client-common/src/main/java/org/apache/hudi/index/HoodieIndex.java) to implement custom indexing.
	- Another key aspect worth understanding is the difference between global and non-global indexes.
		- **Global indexes** enforce uniqueness of keys across all partitions of a table i.e guarantees that exactly one record exists in the table for a given record key. Global indexes offer stronger guarantees, but the update/delete cost grows with size of the table `O(size of table)`, which might still be acceptable for smaller tables.
		-  **Non Global Index** is the default index implementations enforce this constraint only within a specific partition. As one might imagine, non global indexes depends on the writer to provide the same consistent partition path for a given record key during update/delete, but can deliver much better performance since the index lookup operation becomes `O(number of records updated/deleted)` and scales well with write volume.
- File layout
	-   Hudi organizes data tables into a directory structure under a base path on a distributed file system
	-   Tables are broken up into partitions
	-   Within each partition, files are organized into file groups, uniquely identified by a file ID
	-   Each file group contains several file slices
	-   Each slice contains a base file (_.parquet) produced at a certain commit/compaction instant time, along with set of log files (_.log.*) that contain inserts/updates to the base file since the base file was produced.
- Metadata Table, the main purpose of the Metadata Table is to eliminate the requirement for the "list files" operation.
- Multi-modal index can drastically improve the lookup performance in file index and query latency with data skipping.
- Write Operations
	- UPSERT : This is the default operation where the input records are first tagged as inserts or updates by looking up the index, this operation is recommended for use-cases like database change capture where the input almost certainly contains updates. The target table will never show duplicates.
	- INSERT : This operation is very similar to upsert in terms of heuristics/file sizing but completely skips the index lookup step.
	- BULK_INSERT : For initial loading/bootstrapping a Hudi table at first.
	- DELETE : Hudi supports implementing two types of deletes on data stored in Hudi tables, by enabling the user to specify a different record payload implementation.
		- **Soft Deletes** : Retain the record key and just null out the values for all the other fields. This can be achieved by ensuring the appropriate fields are nullable in the table schema and simply upserting the table after setting these fields to null.
		- **Hard Deletes** : A stronger form of deletion is to physically remove any trace of the record from the table. This can be achieved in 3 different ways.
			- Using DataSource, set `OPERATION_OPT_KEY` to `DELETE_OPERATION_OPT_VAL`. This will remove all the records in the DataSet being submitted.
			- Using DataSource, set `PAYLOAD_CLASS_OPT_KEY` to `"org.apache.hudi.EmptyHoodieRecordPayload"`. This will remove all the records in the DataSet being submitted.
			- Using DataSource or DeltaStreamer, add a column named `_hoodie_is_deleted` to DataSet. The value of this column must be set to `true` for all the records to be deleted and either `false` or left null for any records which are to be upserted
	- Write Sequence
		- 1.  [Deduping](https://hudi.apache.org/docs/configurations#hoodiecombinebeforeinsert)
		    1.  First your input records may have duplicate keys within the same batch and duplicates need to be combined or reduced by key.
		2.  [Index Lookup](https://hudi.apache.org/docs/next/indexing)
		    1.  Next, an index lookup is performed to try and match the input records to identify which file groups they belong to.
		3.  [File Sizing](https://hudi.apache.org/docs/next/file_sizing)
		    1.  Then, based on the average size of previous commits, Hudi will make a plan to add enough records to a small file to get it close to the configured maximum limit.
		4.  [Partitioning](https://hudi.apache.org/docs/next/file_layouts)
		    1.  We now arrive at partitioning where we decide what file groups certain updates and inserts will be placed in or if new file groups will be created
		5.  Write I/O
		    1.  Now we actually do the write operations which is either creating a new base file, appending to the log file, or versioning an existing base file.
		6.  Update [Index](https://hudi.apache.org/docs/next/indexing)
		    1.  Now that the write is performed, we will go back and update the index.
		7.  Commit
		    1.  Finally we commit all of these changes atomically. (A [callback notification](https://hudi.apache.org/docs/next/writing_data#commit-notifications) is exposed)
		8.  [Clean](https://hudi.apache.org/docs/next/hoodie_cleaner) (if needed)
		    1.  Following the commit, cleaning is invoked if needed.
		9.  [Compaction](https://hudi.apache.org/docs/next/compaction)
		    1.  If you are using MOR tables, compaction will either run inline, or be scheduled asynchronously
		10.  Archive
		    1.  Lastly, we perform an archival step which moves old [timeline](https://hudi.apache.org/docs/next/timeline) items to an archive folder.
* Schema evolution
	* Scenarios
		1.  Columns (including nested columns) can be added, deleted, modified, and moved.
		2.  Partition columns cannot be evolved.
		3.  You cannot add, delete, or perform operations on nested columns of the Array type.
* Key Generation
	* Every record in Hudi is uniquely identified by a primary key, which is a pair of record key and partition path where the record belongs to. Using primary keys, Hudi can impose
		* Partition level uniqueness integrity constraint
		* Enable fast updates and deletes on records
	* 
have 		

