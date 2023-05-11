When referring to time in a streaming program (for example to define windows), one can refer to different notions of _time_:
* Processing time : Processing time refers to the system time of the machine that is executing the respective operation. When a streaming program runs on processing time, all time-based operations (like time windows) will use the system clock of the machines that run the respective operator.
* Event Time : Event time is the time that each individual event occurred on its producing device. This time is typically embedded within the records. The progress of time depends on the data, not on any wall clocks. _In a perfect world, event time processing would yield completely consistent and deterministic results, regardless of when events arrive, or their ordering. However, unless the events are known to arrive in-order (by timestamp), event time processing incurs some latency while waiting for out-of-order events._ 
	*  Watermarks
		* A stream processor that supports _event time_ needs a way to measure the progress of event time.The mechanism in Flink to measure progress in event time is **watermarks**. Watermarks flow as part of the data stream and carry a timestamp _t_. A _Watermark(t)_ declares that event time has reached time _t_ in that stream, meaning that there should be no more elements from the stream with a timestamp _t’ <= t_ (i.e. events with timestamps older or equal to the watermark).
		* ![[stream_watermark_in_order.svg]]
		* ![[stream_watermark_out_of_order.svg]]
		* ![[parallel_streams_watermarks.svg]]

