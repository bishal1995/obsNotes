### Postgres architecture
AWS RDS For PostgresSQL , VERSION : 13,12

- Replication strategies of interest
	- Write-Ahead Log Shipping : Warm and hot standby servers can be kept current by reading a stream of write-ahead log (WAL) records. If the main server fails, the standby contains almost all of the data of the main server, and can be quickly made the new primary database server. This can be synchronous or asynchronous and can only be done for the entire database server.A standby server can be implemented using file-based log shipping ([Section 27.2](https://www.postgresql.org/docs/current/warm-standby.html "27.2. Log-Shipping Standby Servers")) or streaming replication (see [Section 27.2.5](https://www.postgresql.org/docs/current/warm-standby.html#STREAMING-REPLICATION "27.2.5. Streaming Replication")), or a combination of both. For information on hot standby, see [Section 27.4](https://www.postgresql.org/docs/current/hot-standby.html "27.4. Hot Standby").
	- Logical Replication : Logical replication allows a database server to send a stream of data modifications to another server. PostgreSQL logical replication constructs a stream of logical data modifications from the WAL. Logical replication allows replication of data changes on a per-table basis. In addition, a server that is publishing its own changes can also subscribe to changes from another server, allowing data to flow in multiple directions. For more information on logical replication, see [Chapter 31](https://www.postgresql.org/docs/current/logical-replication.html "Chapter 31. Logical Replication"). Through the logical decoding interface ([Chapter 49](https://www.postgresql.org/docs/current/logicaldecoding.html "Chapter 49. Logical Decoding")), third-party extensions can also provide similar functionality.


-  Read replica limitations with PostgreSQL
	- PostgreSQL read replicas are read-only.
	- Although a read replica isn't a writeable DB instance, you can promote it to become a standalone RDS for PostgreSQL DB instance, it becomes a writable DB instance. It stops receiving write-ahead log (WAL) files from a source DB instance, and it's no longer a read-only instance.
	- You can't create a read replica from another read replica if your RDS for PostgreSQL DB instance is running a PostgreSQL version earlier than 14.1. RDS for PostgreSQL supports cascading read replicas on RDS for PostgreSQL version 14.1 and higher releases only. For more information, see [Using cascading read replicas with RDS for PostgreSQL](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PostgreSQL.Replication.ReadReplicas.html#USER_PostgreSQL.Replication.ReadReplicas.Configuration.cascading).
- Read replica configuration with PostgreSQL
	- RDS for PostgreSQL uses PostgreSQL native streaming replication to create a read-only copy of a source DB instance. This read replica DB instance is an asynchronously created physical replica of the source DB instance. It's created by a special connection that transmits write ahead log (WAL) data from the source DB instance to the read replica. 
-  How streaming replication works for different RDS for PostgreSQL
	- A _physical replication slot_ prevents a source DB instance from removing WAL data before it's consumed by all read replicas. Each read replica has its own physical slot on the source DB instance. The slot keeps track of the oldest WAL (by logical sequence number, LSN) that might be needed by the replica. After all slots and DB connections have progressed beyond a given WAL (LSN), that LSN becomes a candidate for removal at the next checkpoint.
	- Amazon RDS uses Amazon S3 to archive WAL data.
	- 





 #### Enabling CDC with an AWS-managed PostgreSQL DB instance with AWS DMS
 AWS DMS supports CDC on Amazon RDS PostgreSQL databases when the DB instance is configured to use logical replication.









Referrences
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PostgreSQL.Replication.ReadReplicas.html
- https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Source.PostgreSQL.html

