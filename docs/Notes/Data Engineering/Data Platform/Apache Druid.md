
* Good Choices for  druid
	* Insert rates are very high, but updates are less common.
	- You may have more than one table, but each query hits just one big distributed table. Queries may potentially hit more than one smaller "lookup" table.
	- You have high cardinality data columns, e.g. URLs, user IDs, and need fast counting and ranking over them.
	- Your data has a time component. Druid includes optimizations and design choices specifically related to time. 
	- Most of your queries are aggregation and reporting queries. For example "group by" queries. You may also have searching and scanning queries.
* Situations where you would likely _not_ want to use Druid include:
	-   You need low-latency updates of _existing_ records using a primary key. Druid supports streaming inserts, but not streaming updates. You can perform updates using background batch jobs.
	- Big Long Running queries
		- Big Reporting queries.
		- Big Joins


#### Design
* DataSources : Druid data is stored in _datasources_, which are similar to tables in a traditional RDBMS. Each datasource is partitioned by time and, optionally, further partitioned by other attributes. Each time range is called a _chunk_ (for example, a single day, if your datasource is partitioned by day).Each segment is created by a MiddleManager as _mutable_ and _uncommitted_. Data is queryable as soon as it is added to an uncommitted segment.