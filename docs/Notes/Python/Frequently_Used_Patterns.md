- General List
- Sorting a list of tuple on a single element
	```python
	 tup = [(1,2),(3,4)]
	 tup.sort(key = lambda x: x[1]) # Sort it by second element
	 ```
- [Sort list of tuples by specific ordering](https://www.geeksforgeeks.org/python-sort-list-of-tuples-by-specific-ordering)
- Sort list of tuple with multiple keys with precedence, E.g. : Here the tuple list is sorted by following element order : second element , first element 
	```python
	 sorted_lst_of_tuples = sorted(lst_of_tuples, key=lambda x: (x[1], x[0]))
	 ```
 - Initialise an array with known size
	 ```python
	arr = [0]*n
  	``` 
- This