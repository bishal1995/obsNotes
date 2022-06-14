**Stack** is an [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type") that serves as a [collection](https://en.wikipedia.org/wiki/Collection_(abstract_data_type) "Collection (abstract data type)") of elements, with two main principal operations:

-   **Push**, which adds an element to the collection, and
-   **Pop**, which removes the most recently added element that was not yet removed.

![[Data_stack.svg]]

The order in which elements come off a stack gives rise to its alternative name, **LIFO** (**last in, first out**).Additionally, a [peek](https://en.wikipedia.org/wiki/Peek_(data_type_operation) "Peek (data type operation)") operation may give access to the top without modifying the stack

**Monotonic stack** is a stack whose elements are monotonically increasing or descreasing.If we need to pop smaller elements from the stack before pushing a new element, the stack is decreasing from bottom to top.Otherwise, it's increasing from bottom to top.
For example,

	Mono-decreasing Stack
	Before: [5,4,2,1]
	To push 3, we need to pop smaller (or equal) elements first
	After: [5,4,3]


**Queue** is a [collection](https://en.wikipedia.org/wiki/Collection_(abstract_data_type) "Collection (abstract data type)") of entities that are maintained in a sequence and can be modified by the addition of entities at one end of the sequence and the removal of entities from the other end of the sequence.The operations of a queue make it a [first-in-first-out (FIFO) data structure](https://en.wikipedia.org/wiki/FIFO_(computing_and_electronics) "FIFO (computing and electronics)").Queue has  two main principal operations:

- **enque**, add an element to the back
- **deque**, removes an element from the front

![[Data_Queue.svg]]




#### Problems
- [Queue using stack](https://practice.geeksforgeeks.org/problems/queue-using-stack/)
- [Stack using two queues](https://practice.geeksforgeeks.org/problems/stack-using-two-queues/)
- [Next Greater Element - Linear TC](https://leetcode.com/problems/next-greater-element-i/)
- [LRU Cache](https://leetcode.com/problems/lru-cache/)
- [LFU Cache](https://leetcode.com/problems/lfu-cache/)
- 