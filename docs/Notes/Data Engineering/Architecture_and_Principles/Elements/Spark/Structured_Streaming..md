Structured Streaming is a scalable and fault-tolerant stream processing engine built on the Spark SQL engine.Structured Streaming queries are processed using a _micro-batch processing_ engine, which processes data streams as a series of small batch jobs.

#### Programming Model[](https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html#programming-model)
![[structured-streaming-stream-as-a-table.png]]


**Note that Structured Streaming does not materialize the entire table**. It reads the latest available data from the streaming data source, processes it incrementally to update the result, and then discards the source data. It only keeps around the minimal intermediate _state_ data as required to update the result


#### Window Operations on Event Time[](https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html#window-operations-on-event-time)
Aggregations over a sliding event-time window are straightforward with Structured Streaming and are very similar to grouped aggregations. In a grouped aggregation, aggregate values (e.g. counts) are maintained for each unique value in the user-specified grouping column. In case of window-based aggregations, aggregate values are maintained for each window the event-time of a row falls into.
![[structured-streaming-window.png]]

#### Handling Late Data and Watermarking[](https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html#handling-late-data-and-watermarking)
Now consider what happens if one of the events arrives late to the application. For example, say, a word generated at 12:04 (i.e. event time) could be received by the application at 12:11. The application should use the time 12:04 instead of 12:11 to update the older counts for the window `12:00 - 12:10`. This occurs naturally in our window-based grouping – Structured Streaming can maintain the intermediate state for partial aggregates for a long period of time such that late data can update aggregates of old windows correctly.
![[structured-streaming-late-data.png]]
However, to run this query for days, it’s necessary for the system to bound the amount of intermediate in-memory state it accumulates. This means the system needs to know when an old aggregate can be dropped from the in-memory state because the application is not going to receive late data for that aggregate any more. **Watermarking**, which lets the engine automatically track the current event time in the data and attempt to clean up old state accordingly. You can define the watermark of a query by specifying the event time column and the threshold on how late the data is expected to be in terms of event time. For a specific window ending at time `T`, the engine will maintain state and allow late data to update the state until `(max event time seen by the engine - late threshold > T)`. In other words, late data within the threshold will be aggregated, but data later than the threshold will start getting dropped
![[structured-streaming-watermark-append-mode.png]]

