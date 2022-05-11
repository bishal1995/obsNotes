**Recursion** (adjective: _recursive_) occurs when a thing is defined in terms of itself or of its type. In mathematics and computer science, a class of objects or methods exhibits recursive behavior when it can be defined by two properties:

-   A simple _base case_ (or cases) — a terminating scenario that does not use recursion to produce an answer
-   A _recursive step_ — a set of rules that reduces all successive cases toward the base case.

Recursion reduces to one or more similar small problem till a base condition is met.

## Why Recursion Works

In a recursive algorithm, the computer "remembers" every previous state of the problem. This information is "held" by the computer on the **"activation stack"** (i.e., inside of each functions workspace).

Every function has its own workspace **PER CALL** of the function.


## Loops and Tail Recursion

Some recursive algorithms are very similar to loops. These algorithms are called "tail recursive" because the last statement in the algorithm is to "restart" the algorithm. Tail recursive algorithms can be directly translated into loops.