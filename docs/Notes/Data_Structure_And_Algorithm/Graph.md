Graph is a non-linear data structure consisting of vertices and edges. The vertices are sometimes also referred to as nodes and the edges are lines or arcs that connect any two nodes in the graph. More formally a [Graph](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/) is composed of a set of vertices( ****V**** ) and a set of edges( ****E**** ). The graph is denoted by ****G(V, E).****

Type of graph
*  Null Graph : if there are no edges in the graph.
*  Trivial Graph : Graph having only a single vertex
*  Undirected Graph : edges do not have any direction
* Directed Graph :  edge has direction
*  Connected Graph : one node we can visit any other node in the graph
*  Disconnected Graph : at least one node is not reachable from a node
*  Regular Graph : degree of every vertex is equal to K is called K regular graph.
*  Complete Graph : graph in which from each node there is an edge to each other node.
*  Cycle Graph : graph in which the graph is a cycle in itself, the degree of each vertex is 2.
*  Cyclic Graph : graph containing at least one cycle is known as a Cyclic graph.
*  Directed Acyclic Graph : Directed Graph that does not contain any cycle.
*  Bipartite Graph : graph in which vertex can be divided into two sets such that vertex in each set does not contain any edge between them.
* Labeled/Weighted Graph : edges are already specified with suitable weight is known as a weighted graph, can be further classified as directed weighted graphs and undirected weighted graphs.
* Simple Graph: A simple graph is a graph that does not contain more than one edge between the pair of vertices.
* Multi Graph : Any graph which contains some parallel edges but doesn’t contain any self-loop is called a multigraph
	* Parallel Edges: If two vertices are connected with more than one edge then such edges are called parallel edges that are many routes but one destination.
	- Loop: An edge of a graph that starts from a vertex and ends at the same vertex is called a loop or a self-loop.
- Pseudo Graph : A graph G with a self-loop and some multiple edges is called a pseudo graph.
-  **Subgraph** : A graph G1 = (V1, E1) is called a subgraph of a graph G(V, E) if V1(G) is a subset of V(G) and E1(G) is a subset of E(G) such that each edge of G1 has same end vertices as in G.
	- Vertex disjoint subgraph: Any two graph G1 = (V1, E1) and G2 = (V2, E2) are said to be vertex disjoint of a graph G = (V, E) if V1(G1) intersection V2(G2) = null.
	- Edge disjoint subgraph: A subgraph is said to be edge-disjoint if E1(G1) intersection E2(G2) = null.
	- Spanning Subgraph : A spanning subgraph is a subgraph that contains all the vertices of the original graph G that is G'(V’,E’) is spanning if V’=V and E’ is a subset of E.

 Representation of Graphs
 -  Adjacency Matrix
 -  Adjacency List

| Action           | Adjacency Matrix | Adjacency List |
| ---------------- | ---------------- | -------------- |
| Adding Edge      | O(1)             | O(1)           |
| Removing an edge | O(1)             | O(N)           |
| Initializing     | O(N*N)           | O(N)           |
- Graph Traversal
	- Breadth First Search : It explores all the vertices in a graph at the current depth before moving on to the vertices at the next depth level. It starts at a specified vertex and visits all its neighbours before moving on to the next level of neighbours. Applications are
		- Shortest Path Finding: BFS can be used to find the shortest path between two nodes in an unweighted graph. By keeping track of the parent of each node during the traversal, the shortest path can be reconstructed.
		- Cycle Detection: BFS can be used to detect cycles in a graph. If a node is visited twice during the traversal, it indicates the presence of a cycle.
		- Connected Components: BFS can be used to identify connected components in a graph. Each connected component is a set of nodes that can be reached from each other.
		- Topological Sorting: BFS can be used to perform topological sorting on a directed acyclic graph (DAG). Topological sorting arranges the nodes in a linear order such that for any edge (u, v), u appears before v in the order.
		- Level Order Traversal of Binary Trees: BFS can be used to perform a level order traversal of a binary tree. This traversal visits all nodes at the same level before moving to the next level.
		- Network Routing : BFS can be used to find the shortest path between two nodes in a network, making it useful for routing data packets in network protocols.

**Patterns**
- Keeping track of traversed nodes


- Algorithms
	- ![[Union_Find(Disjoint_Set)]]
	- Depth First search : Given a graph, how can we find all of its vertices, and how can we find all paths between two vertices.
		- Either stack or recursion can be used to implement DFS
		- Complexity analysis
			- - Time Complexity: O(V+E)O(V+E). Here, VV represents the number of vertices, and EE represents the number of edges. We need to check every vertex and traverse through every edge in the graph.
			- - Space Complexity: O(V2)O(V2). Either the manually created stack or the recursive call stack can store up to V⋅VV⋅V vertices in the worst case when each vertex has edges connecting to all other vertices because we push vertices to the stack before checking whether they have been visited. 
		- Algorithm : A standard DFS implementation puts each vertex of the graph into one of two categories:
			- Visited
			- Not Visisted
			- The purpose of the algorithm is to mark each vertex as visited while avoiding cycles. The DFS algorithm works as follows
				-  Start by putting any one of the graph's vertices on top of a stack.
				- Take the top item of the stack and add it to the visited list.
				- Create a list of that vertex's adjacent nodes. Add the ones which aren't in the visited list to the top of the stack.
				- Keep repeating steps 2 and 3 until the stack is empty.