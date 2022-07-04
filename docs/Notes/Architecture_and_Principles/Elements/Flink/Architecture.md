Apache Flink is a framework and distributed processing engine for stateful computations over _unbounded and bounded_ data streams.
1.  **Unbounded streams** have a start but no defined end. They do not terminate and provide data as it is generated. Unbounded streams must be continuously processed, i.e., events must be promptly handled after they have been ingested. It is not possible to wait for all input data to arrive because the input is unbounded and will not be complete at any point in time. Processing unbounded data often requires that events are ingested in a specific order, such as the order in which events occurred, to be able to reason about result completeness.
    
2.  **Bounded streams** have a defined start and end. Bounded streams can be processed by ingesting all data before performing any computations. Ordered ingestion is not required to process bounded streams because a bounded data set can always be sorted. Processing of bounded streams is also known as batch processing.

![[bounded-unbounded.png]]

#### Leverage In-Memory Performance

Stateful Flink applications are optimized for local state access. Task state is always maintained in memory or, if the state size exceeds the available memory, in access-efficient on-disk data structures. Hence, tasks perform all computations by accessing local, often in-memory, state yielding very low processing latencies. Flink guarantees exactly-once state consistency in case of failures by periodically and asynchronously checkpointing the local state to durable storage.

![[local-state.png]]

**Streams** can have different characteristics that affect how a stream can and should be processed.
-   **Bounded** and **unbounded** streams: Streams can be unbounded or bounded, i.e., fixed-sized data sets. Flink has sophisticated features to process unbounded streams, but also dedicated operators to efficiently process bounded streams.
-   **Real-time** and **recorded** streams: All data are generated as streams. There are two ways to process the data. Processing it in real-time as it is generated or persisting the stream to a storage system, e.g., a file system or object store, and processed it later. Flink applications can process recorded or real-time streams.


**State**
Every non-trivial streaming application is stateful,Any application that runs basic business logic needs to remember events or intermediate results to access them at a later point in time, for example when the next event is received or after a specific time duration.

![[function-state.png]]

- **Multiple State Primitives**: Flink provides state primitives for different data structures, such as atomic values, lists, or maps.
- **Pluggable State Backends**: Application state is managed in and checkpointed by a pluggable state backend.
- **Exactly-once state consistency**: Flink’s checkpointing and recovery algorithms guarantee the consistency of application state in case of a failure.
- **Very Large State**: Flink is able to maintain application state of several terabytes in size due to its asynchronous and incremental checkpoint algorithm.
- **Scalable Applications**: Flink supports scaling of stateful applications by redistributing the state to more or fewer workers.

**Time**
Most event streams have inherent time semantics because each event is produced at a specific point in time. Moreover, many common stream computations are based on time, such as windows aggregations, sessionization, pattern detection, and time-based joins.
- **Event-time Mode**: Applications that process streams with event-time semantics compute results based on timestamps of the events
- **Watermark Support**: Flink employs watermarks to reason about time in event-time applications.
- **Late Data Handling**: Flink features multiple options to handle late events, such as rerouting them via side outputs and updating previously completed results.
- **Processing-time Mode**: 



**Layered APIs**

![[api-stack.png]]

