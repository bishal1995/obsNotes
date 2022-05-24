**Binary search**, also known as **half-interval search**,[1](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-Williams1976-1) **logarithmic search**,[2](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Binary_search"-2) or **binary chop**,[3](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-FOOTNOTEButterfieldNgondi201646-3) is a [search algorithm](https://en.wikipedia.org/wiki/Search_algorithm "Search algorithm") that finds the position of a target value within a [sorted array](https://en.wikipedia.org/wiki/Sorted_array "Sorted array").[4](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-FOOTNOTECormenLeisersonRivestStein200939-4)[5](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-5) Binary search compares the target value to the middle element of the array. If they are not equal, the half in which the target cannot lie is eliminated and the search continues on the remaining half, again taking the middle element to compare to the target value, and repeating this until the target value is found. If the search ends with the remaining half being empty, the target is not in the array.Binary search runs in [logarithmic time](https://en.wikipedia.org/wiki/Time_complexity#Logarithmic_time "Time complexity") in the [worst case](https://en.wikipedia.org/wiki/Best,_worst_and_average_case "Best, worst and average case"), making O(log n) comparisons, where [n](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the number of elements in the array.[](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-6)

### Procedure

Given an array A {\displaystyle A} ![A](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) of n {\displaystyle n} ![n](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) elements with values or [records](https://en.wikipedia.org/wiki/Record_(computer_science) "Record (computer science)") A 0 , A 1 , A 2 , … , A n − 1 {\displaystyle A_{0},A_{1},A_{2},\ldots ,A_{n-1}} ![{\displaystyle A_{0},A_{1},A_{2},\ldots ,A_{n-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6d8d813e3e6d50ef13e04948e72fcacaf43b7d5c) sorted such that A 0 ≤ A 1 ≤ A 2 ≤ ⋯ ≤ A n − 1 {\displaystyle A_{0}\leq A_{1}\leq A_{2}\leq \cdots \leq A_{n-1}} ![{\displaystyle A_{0}\leq A_{1}\leq A_{2}\leq \cdots \leq A_{n-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/13c473f721041f872e852b4ad816f5ee77b1681d) , and target value T {\displaystyle T} ![T](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) , the following [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine") uses binary search to find the index of T {\displaystyle T} ![T](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) in A {\displaystyle A} ![A](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) .[[7]](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"-8)

1.  Set L {\displaystyle L} ![L](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to 0 {\displaystyle 0} ![0](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) and R {\displaystyle R} ![R](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to n − 1 {\displaystyle n-1} ![n-1](https://wikimedia.org/api/rest_v1/media/math/render/svg/fbd0b0f32b28f51962943ee9ede4fb34198a2521) .
2.  If L > R {\displaystyle L>R} ![{\displaystyle L>R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/145ce1d631364a50d19ac5264c7dc09d4e158b0a) , the search terminates as unsuccessful.
3.  Set m {\displaystyle m} ![m](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) (the position of the middle element) to the [floor](https://en.wikipedia.org/wiki/Floor_and_ceiling_functions "Floor and ceiling functions") of L + R 2 {\displaystyle {\frac {L+R}{2}}} ![{\displaystyle {\frac {L+R}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ed7e052f47e5069015943e2ad3c12363ac155250) , which is the greatest integer less than or equal to L + R 2 {\displaystyle {\frac {L+R}{2}}} ![{\displaystyle {\frac {L+R}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ed7e052f47e5069015943e2ad3c12363ac155250) .
4.  If A m < T {\displaystyle A_{m}<T} ![{\displaystyle A_{m}<T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3f302eb8600e5c6930a74778a3232e4a1c8d91bc) , set L {\displaystyle L} ![L](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to m + 1 {\displaystyle m+1} ![m+1](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6f7ed29a2b4a62d3b6af05cd91a58ffc6094201) and go to step 2.
5.  If A m > T {\displaystyle A_{m}>T} ![{\displaystyle A_{m}>T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8f333a047adf793929566dda96ffdf4493cf3b7) , set R {\displaystyle R} ![R](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to m − 1 {\displaystyle m-1} ![m-1](https://wikimedia.org/api/rest_v1/media/math/render/svg/ecbbd201e0d8f1ccc91cb46362c4b72fa1bbe6c2) and go to step 2.
6.  Now A m = T {\displaystyle A_{m}=T} ![{\displaystyle A_{m}=T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0e65e98f38acc1a2a6e07c43495b3a0058255c6d) , the search is done; return m {\displaystyle m} ![m](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) .

This iterative procedure keeps track of the search boundaries with the two variables L {\displaystyle L} ![L](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) and R {\displaystyle R} ![R](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) . The procedure may be expressed in [pseudocode](https://en.wikipedia.org/wiki/Pseudocode "Pseudocode") as follows, where the variable names and types remain the same as above, `floor` is the [floor function](https://en.wikipedia.org/wiki/Floor_function "Floor function"), and `unsuccessful` refers to a specific value that conveys the failure of the search.[[7]](https://en.wikipedia.org/wiki/Binary_search_algorithm#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"-8)

- **function** binary_search(A, n, T) **is**
	- L := 0
	- R := n − 1
	- **while** L ≤ R **do**
		- m := floor((L + R) / 2)
		- **if** A[m] < T **then**
			- L := m + 1
		- **else if** A[m] > T **then**
			- R := m − 1
		- **else**:
			- **return** m
	- **return** unsuccessful



### Problems
- [Nth Root Of M Using Binary Search](https://www.codingninjas.com/codestudio/problems/1062679)
- 2D Matrix
	- [Find Median](https://www.codingninjas.com/codestudio/problems/873378)
	- [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) - [Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)
- 


### Refer https://www.geeksforgeeks.org/divide-and-conquer/ For Binary search problems