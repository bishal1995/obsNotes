A ****Binary Search Tree**** is a data structure used in computer science for organizing and storing data in a sorted manner. Each node in a ****Binary Search Tree**** has at most two children, a ****left**** child and a ****right**** child, with the ****left**** child containing values less than the parent node and the ****right**** child containing values greater than the parent node. This hierarchical structure allows for efficient ****searching****, ****insertion****, and ****deletion**** operations on the data stored in the tree.

![[Pasted image 20240412070246.png]]
* Properties
	* The left subtree of a node contains only nodes with keys lesser than the node’s key.
	* The right subtree of a node contains only nodes with keys greater than the node’s key.
	* The left and right subtree each must also be a binary search tree
* Traversal
	* InOrder traversal if an BST returns the values in a sorted manner