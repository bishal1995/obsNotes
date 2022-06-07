In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a **stack** is an [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type") that serves as a [collection](https://en.wikipedia.org/wiki/Collection_(abstract_data_type) "Collection (abstract data type)") of elements, with two main principal operations:

-   **Push**, which adds an element to the collection, and
-   **Pop**, which removes the most recently added element that was not yet removed.


**Monotonic stack** is a stack whose elements are monotonically increasing or descreasing.If we need to pop smaller elements from the stack before pushing a new element, the stack is decreasing from bottom to top.Otherwise, it's increasing from bottom to top.
For example,

	Mono-decreasing Stack
	Before: [5,4,2,1]
	To push 3, we need to pop smaller (or equal) elements first
	After: [5,4,3]

#### Problems
- [Queue using stack](https://practice.geeksforgeeks.org/problems/queue-using-stack/)
- [Stack using two queues](https://practice.geeksforgeeks.org/problems/stack-using-two-queues/)
- [Next Greater Element - Linear TC](https://leetcode.com/problems/next-greater-element-i/)
- [LRU Cache](https://leetcode.com/problems/lru-cache/)
- 