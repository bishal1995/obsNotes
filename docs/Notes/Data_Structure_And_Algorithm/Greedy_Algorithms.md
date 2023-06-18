#### Optimal Substructure
A problem exhibits optimal substructure if an optimal solution to the problem contains within it optimal solutions to subproblems.


#### Identify a problem to be solved by greedy approach
Most problems for which they work will have two properties
* **`Greedy choice property`** : When we are considering which choice to make, we make the choice that looks best in the current problem, without considering results from subproblems. We can assemble a globally optimal solution by making locally optimal (greedy) choices.
* **`Optimal sunstructure`** : A problem exhibits this property if an optimal solution to the problem contains within it optimal solutions to subproblems.

#### Steps to design a greedy solution
* Cast the optimisation problem as one in which we make a choice and are left with one subproblem to solve.
* Prove that there is always an optimal solution to the original problem that makes the greedy choice, so that the greedy choice is always safe.
* Demonstrate optimal substructure by showing that, having made the greedy choice, what remains is a subproblem with the property that if we combine an optimal solution to the subproblem with the greedy choice we have made, we arrive at an optimal solution to the original problem.


 For interview it is important to remember the patterns, as it hard to prove that the problem can be solved by greedy approach

## Different Types of Greedy Algorithm [Programiz](https://www.programiz.com/dsa/greedy-algorithm) list

-   [Selection Sort](https://www.programiz.com/dsa/selection-sort)
-   [Knapsack Problem](https://en.wikipedia.org/wiki/Knapsack_problem)
-   [Minimum Spanning Tree](https://www.programiz.com/dsa/spanning-tree-and-minimum-spanning-tree)
-   [Single-Source Shortest Path Problem](https://en.wikipedia.org/wiki/Shortest_path_problem)
-   Job Scheduling Problem
-   [Prim's Minimal Spanning Tree Algorithm](https://www.programiz.com/dsa/prim-algorithm)
-   [Kruskal's Minimal Spanning Tree Algorithm](https://www.programiz.com/dsa/kruskal-algorithm)
-   [Dijkstra's Minimal Spanning Tree Algorithm](https://www.programiz.com/dsa/dijkstra-algorithm)
-   [Huffman Coding](https://www.programiz.com/dsa/huffman-coding)
-   [Ford-Fulkerson Algorithm](https://www.programiz.com/dsa/ford-fulkerson-algorithm)


##  Problem List (Vague cluster)
- Standard Greedy Algorithms 
	- [[Intervals]]
		- [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)/  [Minimum Platforms](https://practice.geeksforgeeks.org/problems/minimum-platforms-1587115620/1#))[ Activity Selection Problem ](https://www.geeksforgeeks.org/activity-selection-problem-greedy-algo-1/) / [ Meeting Room ](https://leetcode.com/problems/meeting-rooms/) / 
	- [Greedy Algorithm for Egyptian Fraction](https://www.geeksforgeeks.org/greedy-algorithm-egyptian-fraction/)
	- [Job Sequencing Problem]
		- Max Profit and number of Jobs [GFG](https://www.geeksforgeeks.org/job-sequencing-problem/) / [CodingNinja](https://www.codingninjas.com/codestudio/problems/job-sequencing-problem_1169460)
		- 
	- [Fractional Knapsack Problem](https://practice.geeksforgeeks.org/problems/fractional-knapsack-1587115620/)
	- [Find Minimum Number Of Coins](https://www.codingninjas.com/codestudio/problems/975277)
	- 