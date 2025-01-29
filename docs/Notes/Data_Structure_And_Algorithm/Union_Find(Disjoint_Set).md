![[Pasted image 20240518105930.png]]
**Terminologies**
- Parent node: the direct parent node of a vertex. For example, in Figure 5, the parent node of vertex 3 is 1, the parent node of vertex 2 is 0, and the parent node of vertex 9 is 9.
- Root node: a node without a parent node; it can be viewed as the parent node of itself. For example, in Figure 5, the root node of vertices 3 and 2 is 0. As for 0, it is its own root node and parent node. Likewise, the root node and parent node of vertex 9 is 9 itself. Sometimes the root node is referred to as the head node.



General Steps
- **The `find` function** finds the root node of a given vertex
- **The `union` function** unions two vertices and makes their root nodes the same

There are two ways to implement a “disjoint set”.
- Implementation with Quick Find: 
	- Data Structure :  An Array with index representing the vertex and the the value for a given index is the Root Vertex of it
	- Time Complexity
		- Find : O(n)
		- Union : O(n^2)
- Implementation with Quick Union: 
	- Data Structure : An Array with index representing the vertex and the the value for a given index is the Root or parent Vertex of it
	- compared with the Quick Find implementation, the time complexity of the `union` function is better. Meanwhile, the `find` function will take more time in this case.