A **heap** is a specialized [tree](https://en.wikipedia.org/wiki/Tree_(data_structure)"Tree (data structure)"-based [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure")which is essentially an [almost complete](https://en.wikipedia.org/wiki/Heap_(data_structure)#cite_note-1) (When a heap is a complete binary tree, it has a smallest possible height—a heap with _N_ nodes and _a_ branches for each node always has log__a__N height.This property of Binary Heap makes them suitable to be stored in an array.)tree that satisfies the **heap property**: in a _max heap_, for any given [node](https://en.wikipedia.org/wiki/Node_(computer_science) "Node (computer science)" C, if P is a parent node of C, then the _key_ (the _value_) of P is greater than or equal to the key of C. In a _min heap_, the key of P is less than or equal to the key of C.(https://en.wikipedia.org/wiki/Heap) The node at the "top" of the heap (with no parents) is called the _root_ node.

A complete binary tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes at the last level h. A perfect tree is therefore always complete but a complete tree is not necessarily perfect. An alternative definition is a perfect tree whose rightmost leaves (perhaps all) have been removed. Some authors use the term complete to refer instead to a perfect binary tree as defined above, in which case they call this type of tree (with a possibly not filled last level) an almost complete binary tree or nearly complete binary tree. A complete binary tree can be efficiently represented using an array.

The heap is one maximally efficient implementation of an [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type") called a [priority queue](https://en.wikipedia.org/wiki/Priority_queue "Priority queue"), and in fact, priority queues are often referred to as "heaps", regardless of how they may be implemented. In a heap, the highest (or lowest) priority element is always stored at the root. However, a heap is not a sorted structure; it can be regarded as being partially ordered.

A common implementation of a heap is the [binary heap](https://en.wikipedia.org/wiki/Binary_heap "Binary heap"), in which the tree is a [binary tree](https://en.wikipedia.org/wiki/Binary_tree)
![[Max-Heap-new.svg]]
The common operations involving heaps are:

Basic

-   _find-max_ (or _find-min_): find a maximum item of a max-heap, or a minimum item of a min-heap, respectively (a.k.a. _[peek](https://en.wikipedia.org/wiki/Peek_(data_type_operation) "Peek (data type operation)")_)
-   _insert_: adding a new key to the heap (a.k.a., _push_[[4]](https://en.wikipedia.org/wiki/Heap_(data_structure)#cite_note-4))
-   _extract-max_ (or _extract-min_): returns the node of maximum value from a max heap [or minimum value from a min heap] after removing it from the heap (a.k.a., _pop_[[5]](https://en.wikipedia.org/wiki/Heap_(data_structure)#cite_note-5))
-   _delete-max_ (or _delete-min_): removing the root node of a max heap (or min heap), respectively
-   _replace_: pop root and push a new key. More efficient than pop followed by push, since only need to balance once, not twice, and appropriate for fixed-size heaps.[[6]](https://en.wikipedia.org/wiki/Heap_(data_structure)#cite_note-6)

Creation

-   _create-heap_: create an empty heap
-   _heapify_: create a heap out of given array of elements
-   _merge_ (_union_): joining two heaps to form a valid new heap containing all the elements of both, preserving the original heaps.
-   _meld_: joining two heaps to form a valid new heap containing all the elements of both, destroying the original heaps.

Inspection

-   _size_: return the number of items in the heap.
-   _is-empty_: return true if the heap is empty, false otherwise.

Internal

-   _increase-key_ or _decrease-key_: updating a key within a max- or min-heap, respectively
-   _delete_: delete an arbitrary node (followed by moving last node and sifting to maintain heap)
-   _sift-up_: move a node up in the tree, as long as needed; used to restore heap condition after insertion. Called "sift" because node moves up the tree until it reaches the correct level, as in a [sieve](https://en.wikipedia.org/wiki/Sieve "Sieve").
-   _sift-down_: move a node down in the tree, similar to sift-up; used to restore heap condition after deletion or replacement.


#### Array Representation
![[binaryheap.png]]

. A binary heap is typically represented as an array.

-   The root element will be at Arr[0].
-   Below table shows indexes of other nodes for the ith node, i.e., Arr[i]:  
	- Arr[(i-1)/2]  Returns the parent node
	- Arr[(2*i)+1] Returns the left child node
	- Arr[(2*i)+2]  Returns the right child node






### Problems
- Heap Implementation
- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
	- [Unique Elements](https://leetcode.com/problems/kth-largest-element-in-an-array/)
	- [Repeated Elements](https://leetcode.com/problems/find-the-kth-largest-integer-in-the-array/)
- [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
- 