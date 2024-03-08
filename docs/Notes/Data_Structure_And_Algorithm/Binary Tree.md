
A **Binary Tree Data Structure** is a hierarchical data structure in which each node has at most two children, referred to as the left child and the right child. It is commonly used in computer science for efficient storage and retrieval of data, with various operations such as insertion, deletion, and traversal.The topmost node in a binary tree is called the root, and the bottom-most nodes are called leaves.

**Representation of Binary Tree****
Each node in the tree contains the following:
-  Data
-  Pointer to the left child
-  Pointer to the right child

**Basic Operations On Binary Tree:**
- Inserting an element.
- Removing an element.
- Searching for an element.
- Deletion for an element.
- Traversing an element.

 **Auxiliary Operations On Binary Tree:**
-  Finding the height of the tree
-  Find the level of the tree
-  Finding the size of the entire tree.





### Very important to understand is the order of function calls (Stack generated during the tree traversal).




* Tree traversal
	* Pre Order traversal **1 -> 2 -> 4 -> 5 -> 3 -> 6**.
		* ![[Pasted image 20240222083104.png]] 
	*  In Order **4 -> 2 -> 5 -> 1 -> 3 -> 6**.
		* ![[Pasted image 20240222091827.png]]
	* Post Order Traversal **4 -> 5 -> 2 -> 6 -> 3 -> 1**.
		* ![[Pasted image 20240222091954.png]]




* Array Implementation of Binary tree [Link](https://www.geeksforgeeks.org/binary-tree-array-implementation/)

```
 Case 1:** (0 -> n-1) 
 
	if (say)father=p; 
	then left_son=(2*p)+1; 
	and right_son=(2*p)+2;

       A(0)    
     /   \
    B(1)  C(2)  
  /   \      \
 D(3)  E(4)   F(6)


Case 2:** (1 —> n)

	if (say)father=p; 
	then left_son=(2*p); 
	and right_son=(2*p)+1;
	
      A(1)    
     /   \
    B(2)  C(3)  
  /   \      \
 D(4)  E(5)   F(7)
```

