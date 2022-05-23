**Backtracking** is a general [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") for finding solutions to some [computational problems](https://en.wikipedia.org/wiki/Computational_problem "Computational problem"), notably [constraint satisfaction problems](https://en.wikipedia.org/wiki/Constraint_satisfaction_problem "Constraint satisfaction problem"), that incrementally builds candidates to the solutions, and abandons a candidate ("backtracks") as soon as it determines that the candidate cannot possibly be completed to a valid solution.
Backtracking can be applied only for problems which admit the concept of a "partial candidate solution" and a relatively quick test of whether it can possibly be completed to a valid solution. It is useless, for example, for locating a given value in an unordered table. When it is applicable, however, backtracking is often much faster than [brute-force enumeration](https://en.wikipedia.org/wiki/Brute-force_search "Brute-force search") of all complete candidates, since it can eliminate many candidates with a single test.
Backtracking is an important tool for solving [constraint satisfaction problems](https://en.wikipedia.org/wiki/Constraint_satisfaction_problem "Constraint satisfaction problem"),[2](https://en.wikipedia.org/wiki/Backtracking#cite_note-BiereHeule2009-2) such as [crosswords](https://en.wikipedia.org/wiki/Crosswords "Crosswords"), [verbal arithmetic](https://en.wikipedia.org/wiki/Verbal_arithmetic "Verbal arithmetic"), [Sudoku](https://en.wikipedia.org/wiki/Algorithmics_of_sudoku "Algorithmics of sudoku"), and many other puzzles. It is often the most convenient technique for [parsing](https://en.wikipedia.org/wiki/Parsing "Parsing"),[3](https://en.wikipedia.org/wiki/Backtracking#cite_note-Watson2017-3) for the [knapsack problem](https://en.wikipedia.org/wiki/Knapsack_problem "Knapsack problem") and other [combinatorial optimization](https://en.wikipedia.org/wiki/Combinatorial_optimization "Combinatorial optimization") problems.
Backtracking depends on user-given "[black box procedures](https://en.wikipedia.org/wiki/Procedural_parameter "Procedural parameter")" that define the problem to be solved, the nature of the partial candidates, and how they are extended into complete candidates. It is therefore a [metaheuristic](https://en.wikipedia.org/wiki/Metaheuristic "Metaheuristic") rather than a specific algorithm – although, unlike many other meta-heuristics, it is guaranteed to find all solutions to a finite problem in a bounded amount of time.

The backtracking algorithm enumerates a set of _partial candidates_ that, in principle, could be _completed_ in various ways to give all the possible solutions to the given problem. The completion is done incrementally, by a sequence of _candidate extension steps._

Conceptually, the partial candidates are represented as the nodes of a [tree structure](https://en.wikipedia.org/wiki/Tree_structure "Tree structure"), the _potential search tree._ Each partial candidate is the parent of the candidates that differ from it by a single extension step; the leaves of the tree are the partial candidates that cannot be extended any further.

The backtracking algorithm traverses this search tree [recursively](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)"), from the root down, in [depth-first order](https://en.wikipedia.org/wiki/Depth-first_search "Depth-first search"). At each node _c_, the algorithm checks whether _c_ can be completed to a valid solution. If it cannot, the whole sub-tree rooted at _c_ is skipped (_pruned_). Otherwise, the algorithm (1) checks whether _c_ itself is a valid solution, and if so reports it to the user; and (2) recursively enumerates all sub-trees of _c_. The two tests and the children of each node are defined by user-given procedures.

Therefore, the _actual search tree_ that is traversed by the algorithm is only a part of the potential tree. The total cost of the algorithm is the number of nodes of the actual tree times the cost of obtaining and processing each node. This fact should be considered when choosing the potential search tree and implementing the pruning test.

### Pseudocode

In order to apply backtracking to a specific class of problems, one must provide the data _P_ for the particular instance of the problem that is to be solved, and six [procedural parameters](https://en.wikipedia.org/wiki/Procedural_parameter "Procedural parameter"), _root_, _reject_, _accept_, _first_, _next_, and _output_. These procedures should take the instance data _P_ as a parameter and should do the following:

1.  _root_(_P_): return the partial candidate at the root of the search tree.
2.  _reject_(_P_,_c_): return _true_ only if the partial candidate _c_ is not worth completing.
3.  _accept_(_P_,_c_): return _true_ if _c_ is a solution of _P_, and _false_ otherwise.
4.  _first_(_P_,_c_): generate the first extension of candidate _c_.
5.  _next_(_P_,_s_): generate the next alternative extension of a candidate, after the extension _s_.
6.  _output_(_P_,_c_): use the solution _c_ of _P_, as appropriate to the application.

The backtracking algorithm reduces the problem to the call _backtrack_(_root_(_P_)), where _backtrack_ is the following recursive procedure:

- procedure backtrack(c) **is**
	- if reject(P, c) **then** return
	- if accept(P, c) **then** output(P, c)
	- s ← first(P, c)
	- while s ≠ NULL **do**
		- backtrack(s)
		- s ← next(P, s)
		
### Problems
- [N Queen Problem](https://leetcode.com/problems/n-queens/)
- [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)
- [Rat in a Maze Problem](https://practice.geeksforgeeks.org/problems/rat-in-a-maze-problem) **good question**
- [Map Coloring Problem](https://www.codingninjas.com/codestudio/problems/981273)