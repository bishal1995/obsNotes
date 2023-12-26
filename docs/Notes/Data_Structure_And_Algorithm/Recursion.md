**Recursion** (adjective: _recursive_) occurs when a thing is defined in terms of itself or of its type. In mathematics and computer science, a class of objects or methods exhibits recursive behavior when it can be defined by two properties:

-   A simple _base case_ (or cases) — a terminating scenario that does not use recursion to produce an answer
-   A _recursive step_ — a set of rules that reduces all successive cases toward the base case.

Recursion reduces to one or more similar small problem till a base condition is met.


## Memory Allocation
When any function is called from main(), the memory is allocated to it on the stack. A recursive function calls itself, the memory for a called function is allocated on top of memory allocated to calling function and different copy of local variables is created for each function call. When the base case is reached, the function returns its value to the function by whom it is called and memory is de-allocated and the process continues.

## Tailed recursion
A recursive function is tail recursive when recursive call is the last thing executed by the function.The tail recursive functions considered better than non tail recursive functions as tail-recursion can be optimized by the compiler. Compilers usually execute recursive procedures by using a **stack**. This stack consists of all the pertinent information, including the parameter values, for each recursive call. When a procedure is called, its information is **pushed** onto a stack, and when the function terminates the information is **popped** out of the stack. Thus for the non-tail-recursive functions, the **stack depth** (maximum amount of stack space used at any time during compilation) is more. The idea used by compilers to optimize tail-recursive functions is simple, since the recursive call is the last statement, there is nothing left to do in the current function, so saving the current function’s stack frame is of no use.

## Why Recursion Works

In a recursive algorithm, the computer "remembers" every previous state of the problem. This information is "held" by the computer on the **"activation stack"** (i.e., inside of each functions workspace).

Every function has its own workspace **PER CALL** of the function.


## General Observation/Techniques
-	Try to visualise the problem in terms of recursion tree representation of the problem
	-	Try guessing the time and space Complexity
	-	


## Loops and Tail Recursion
Some recursive algorithms are very similar to loops. These algorithms are called "tail recursive" because the last statement in the algorithm is to "restart" the algorithm. Tail recursive algorithms can be directly translated into loops.


Questions
* Tower of Hanoo
* Inorder/PreOrder/PostOrder traversal of a tree.


- Subset
	- [Generate Subset](https://leetcode.com/problems/subsets-ii/)
	- [Subset Sum](https://practice.geeksforgeeks.org/problems/subset-sums2234)
- [Combination Sum](https://leetcode.com/problems/combination-sum/) Good Question
- [All Permutations](https://leetcode.com/problems/permutations/)
- [Print all possible expressions that evaluate to a target(Similar)Todo](https://leetcode.com/problems/24-game/) [GFG](https://leetcode.com/problems/24-game/)
- [Generate all binary strings without consecutive 1’s *Todo*](https://www.geeksforgeeks.org/generate-binary-strings-without-consecutive-1s/)
- [Recursive solution to count substrings with same first and last characters *Todo*](https://www.geeksforgeeks.org/recursive-solution-count-substrings-first-last-characters/)
- [Combinations in a String of Digits *Todo*](https://www.geeksforgeeks.org/combinations-string-digits/)
- [Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)
- [Palindrome partitioning](https://leetcode.com/problems/palindrome-partitioning/) , [GFG](https://www.geeksforgeeks.org/palindrome-partitioning-dp-17/?ref=lbp) Using recursion
- Median of 2 sorted Array
	- Same Size
	- Different Size
		- Linear(Merge both array), Time Complexity `O(m+n)`, Auxiliary Space `O(1)`
		- Using Binary Search, Time Complexity `O(min(log m, log n))` ,Auxiliary Space `O(1)`
		- Problems
			- [Leetcode - `O(log (m+n))`](https://leetcode.com/problems/median-of-two-sorted-arrays/)
- Matrix Multiplication
	- 

