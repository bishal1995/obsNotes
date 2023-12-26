## Synchronization as a problem  

Some solutions deal with synchronization by allowing only one server to modify the data. Servers that can modify data are called read/write, master or primary servers. Servers that track changes in the primary are called standby or secondary servers. A standby server that cannot be connected to until it is promoted to a primary server is called a warm standby server, and one that can accept connections and serves read-only queries is called a hot standby server.

### Solutions

Write-Ahead Log Shipping Warm and hot standby servers can be kept current by reading a stream of write-ahead log (WAL) records. If the main server fails, the standby contains almost all of the data of the main server, and can be quickly made the new primary database server. This can be synchronous or asynchronous and can only be done for the entire database server. A standby server can be implemented using file-based log shipping (Section 27.2) or streaming replication (see Section 27.2.5), or a combination of both. For information on hot standby, see Section 27.4. Logical Replication Logical replication allows a database server to send a stream of data modifications to another server. PostgreSQL logical replication constructs a stream of logical data modifications from the WAL. Logical replication allows replication of data changes on a per-table basis. In addition, a server that is publishing its own changes can also subscribe to changes from another server, allowing data to flow in multiple directions. For more information on logical replication, see Chapter 31. Through the logical decoding interface (Chapter 49), third-party extensions can also provide similar functionality. Other can be referred from :

Log Shipping : 27.2. Log-Shipping Standby Servers Types: File based : WAL files are shipped Streaming replication : WAL records are Preparing the primary for standby servers : If you want to use streaming replication, set up authentication on the primary server to allow replication connections from the standby server(s); that is, create a role and provide a suitable entry or entries in pg_hba.conf with the database field set to replication. Also ensure max_wal_senders is set to a sufficiently large value in the configuration file of the primary server. If replication slots will be used, ensure that max_replication_slots is set sufficiently high as well.



:joy:

