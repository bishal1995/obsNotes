A **heap** is a specialized [tree](https://en.wikipedia.org/wiki/Tree_(data_structure)"Tree (data structure)"-based [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure")which is essentially an [almost complete](https://en.wikipedia.org/wiki/Heap_(data_structure)#cite_note-1) (When a heap is a complete binary tree, it has a smallest possible height—a heap with _N_ nodes and _a_ branches for each node always has log__a__N height.This property of Binary Heap makes them suitable to be stored in an array.)tree that satisfies the **heap property**: in a _max heap_, for any given [node](https://en.wikipedia.org/wiki/Node_(computer_science) "Node (computer science)" C, if P is a parent node of C, then the _key_ (the _value_) of P is greater than or equal to the key of C. In a _min heap_, the key of P is less than or equal to the key of C.(https://en.wikipedia.org/wiki/Heap) The node at the "top" of the heap (with no parents) is called the _root_ node.

A complete binary tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes at the last level h. A perfect tree is therefore always complete but a complete tree is not necessarily perfect. An alternative definition is a perfect tree whose rightmost leaves (perhaps all) have been removed. Some authors use the term complete to refer instead to a perfect binary tree as defined above, in which case they call this type of tree (with a possibly not filled last level) an almost complete binary tree or nearly complete binary tree. A complete binary tree can be efficiently represented using an array.

The heap is one maximally efficient implementation of an [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type") called a [priority queue](https://en.wikipedia.org/wiki/Priority_queue "Priority queue"), and in fact, priority queues are often referred to as "heaps", regardless of how they may be implemented. In a heap, the highest (or lowest) priority element is always stored at the root. However, a heap is not a sorted structure; it can be regarded as being partially ordered.

A common implementation of a heap is the [binary heap](https://en.wikipedia.org/wiki/Binary_heap "Binary heap"), in which the tree is a [binary tree](https://en.wikipedia.org/wiki/Binary_tree)
![[Max-Heap-new.svg]]
### Refer CLRS (Ch. Heapsort)
A binary heap is typically represented as an array.A priority queue is a data structure for maintaining a set S of elements, each with an associated value called a key.An array Arr that represents a heap is an object with two at-
tributes: Arr.length, which (as usual) gives the number of elements in the array, and Arr.heap-size, which represents how many elements in the heap are stored within array A. That is, although Arr[1 ... Arr.length] may contain numbers, only the elements in Arr[1 ... Arr.heap-size], where 0 <= A:heap-size <= A:length, are valid elements of the heap.

-   The root elem     ent will be at Arr[0].
-   Below table shows indexes of other nodes for the ith node, i.e., Arr[i]:  
	- Parent(i) : Arr[ (i-1)/2 ]  Returns the parent node
	- Left(i) : Arr[(2*i) + 1] Returns the left child node
	- Right(i) : Arr[(2*i)+2]  Returns the right child node


* Heap operations (Max-Heap example)
	* maxHeapify(Arr,i) : Mantain min/max heap property for a given array and an element - `O(Log n)`
		* When it is called, MAX-HEAPIFY assumes that the binary trees rooted at LEFT[i] and RIGHT[i] are max-heaps, but that Arr[i] might be smaller than its children, thus violating the max-heap property. MAX-HEAPIFY lets the value at Arr[i] “ﬂoat down” in the max-heap so that the subtree rooted at index i obeys the max-heap property.
	* buildMaxHeap() : For given element build a heap,Since the leaves are the nodes indexed by floor(n/2) , floor(n/2) + 1, floor(n/2) + 2, ... n, so each lement is a one element heap to begin with, we run the maxHeapify() in a bottom-up approach to build the heap. Refer CLRS(3rd Edition) 6.3 to find proof.
	* extractMax() : Removes and returns the root - `O(Log n)`
	* inreaseKey(Arr,i,j) : Increase the key i to j. - `O(Log n)`
	* insertKey(Arr,i) : Insert a element with key i.
	* getMax() :  Return the root node.
	* deleteKey(Arr, i) : Deletes a key i. 


### Problems
- [Heap Implementation](https://practice.geeksforgeeks.org/problems/operations-on-binary-min-heap/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=operations-on-binary-min-heap)
- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
	- [Unique Elements](https://leetcode.com/problems/kth-largest-element-in-an-array/)
	- [Repeated Elements](https://leetcode.com/problems/find-the-kth-largest-integer-in-the-array/)
- [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
- 