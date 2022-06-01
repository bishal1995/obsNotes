A **divide-and-conquer** [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") [recursively](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)") breaks down a problem into two or more sub-problems of the same or related type, until these become simple enough to be solved directly. The solutions to the sub-problems are then combined to give a solution to the original problem.
The name divide and conquer is sometimes applied to algorithms that reduce each problem to only one sub-problem, such as the [binary search](https://en.wikipedia.org/wiki/Binary_search "Binary search").The name **decrease and conquer** has been proposed instead for the single-subproblem class.
On the other hand, efficiency often improves if the recursion is stopped at relatively large base cases, and these are solved non-recursively, resulting in a [hybrid algorithm](https://en.wikipedia.org/wiki/Hybrid_algorithm "Hybrid algorithm"). This strategy avoids the overhead of recursive calls that do little or no work and may also allow the use of specialized non-recursive algorithms that, for those base cases, are more efficient than explicit recursion. A general procedure for a simple hybrid recursive algorithm is _short-circuiting the base case_, also known as _[arm's-length recursion](https://en.wikipedia.org/wiki/Arm%27s-length_recursion "Arm's-length recursion")_. In this case, whether the next step will result in the base case is checked before the function call, avoiding an unnecessary function call. For example, in a tree, rather than recursing to a child node and then checking whether it is null, checking null before recursing; avoids half the function calls in some algorithms on binary trees.
For some problems, the branched recursion may end up evaluating the same sub-problem many times over. In such cases it may be worth identifying and saving the solutions to these overlapping subproblems, a technique is commonly known as [memoization](https://en.wikipedia.org/wiki/Memoization "Memoization").







### Problems
- Find Median
	- [Median of Two Sorted Arrays of Same Size](https://www.geeksforgeeks.org/median-of-two-sorted-arrays/) expected TC :  O(log(n))
	- [Median of Two Sorted Arrays of Different Size - LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/) [GFG](https://www.geeksforgeeks.org/median-of-two-sorted-arrays-of-different-sizes/)
- Greatest Common Divisor
- Multiply 2 n digit number - Karatsuba [Leetcode](https://leetcode.com/problems/multiply-strings/)[GFG](https://www.geeksforgeeks.org/karatsuba-algorithm-for-fast-multiplication-using-divide-and-conquer-algorithm/)
- Matrix Multiplication - Strassen [GFG](https://www.geeksforgeeks.org/strassens-matrix-multiplication/)
- Tower Of Hanoi
- [Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)
- Peak Element
	- [In 1D Array](https://leetcode.com/problems/find-peak-element/)
	- [In 2D Array](https://leetcode.com/problems/find-a-peak-element-ii/)
- [Find Array Given Subset Sums](https://leetcode.com/problems/find-array-given-subset-sums/)
- Closest Point
	- [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/) 
	- GFG [1](https://www.geeksforgeeks.org/closest-pair-of-points-using-divide-and-conquer-algorithm/) [2](https://www.geeksforgeeks.org/closest-pair-of-points-onlogn-implementation/)
	- 
- The Skyline Problem [Leetcode](https://leetcode.com/problems/top-k-frequent-elements/) [GFG](https://www.geeksforgeeks.org/the-skyline-problem-using-divide-and-conquer-algorithm/)
- Convex Hull [LeetCode](https://leetcode.com/problems/erect-the-fence/)[GFG](https://www.geeksforgeeks.org/convex-hull-using-divide-and-conquer-algorithm/)
- 