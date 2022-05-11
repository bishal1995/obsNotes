**Recursion** (adjective: _recursive_) occurs when a thing is defined in terms of itself or of its type. In mathematics and computer science, a class of objects or methods exhibits recursive behavior when it can be defined by two properties:

-   A simple _base case_ (or cases) — a terminating scenario that does not use recursion to produce an answer
-   A _recursive step_ — a set of rules that reduces all successive cases toward the base case.

For example, the following is a recursive definition of a person's _ancestor_. One's ancestor is either:

-   One's parent (_base case_), _or_
-   One's parent's ancestor (_recursive step_).