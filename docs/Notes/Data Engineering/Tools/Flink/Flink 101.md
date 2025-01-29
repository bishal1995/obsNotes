What it does :  **Stateful Computations over Data Streams**
How it does : 















![[Screenshot from 2024-05-14 09-06-47.png]]

Stream processing
To analyze data, you can either organize your processing around `bounded` or `unbounded` streams,
- Bounded Stream : It is the paradigm at work when you process a bounded data stream. In this mode of operation you can choose to ingest the entire dataset before producing any results, which means that it is possible, for example, to sort the data, compute global statistics, or produce a final report that summarizes all of the input.
- Unbounded Stream : It involves unbounded data streams. Conceptually, at least, the input may never end, and so you are forced to continuously process the data as it arrives.
In Flink, applications are composed of **streaming dataflows** that may be transformed by user-defined **operators**. These dataflows form directed graphs that start with one or more **sources**, and end in one or more **sinks**.
- ![[program_dataflow.svg]]

