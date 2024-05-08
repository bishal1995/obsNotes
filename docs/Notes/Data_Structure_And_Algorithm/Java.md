Most commonly used data structure
* Operator
```java
/*
Logical
	And : &&
	OR  : ||
*/
```
* Type casting
```
long k = (long)2147483647 
```
* Array
```java
int[] arr = new int[10]; // value initialised with zero
// Slicing a array
int[] arr = {10, 20, 30, 40, 50};
Arrays.copyOfRange(arr, 1, 4); // returns {20, 30, 40}
// Declaring a array of array and assigning value;
int[][] op = new int[4][2];
op[0] = new int[]{1,2};
```
* List
```java
// Declaring a empty list
List<Integer> intList = new ArrayList<Integer>();
// Adding a element
intList.add(69);
// Declaring a list of list
List<List<Integer>> levels = new ArrayList<List<Integer>>();
```
* HashMap
```java
// Import
import java.util.HashMap;
// declaring a empty HashMap
HashMap<String, Integer> strIntHashMap = new HashMap<String, Integer>();
// Adding an element
strIntHashMap.put("key1",1);
strIntHashMap.put("key2",2);
// Getting an element
strIntHashMap.get("key1");
// Checking a key in the HashMap
strIntHashMap.containsKey("key1") ; // returns True
// Removeing a key
strIntHashMap.remove("key1") ; // returns True
// Iterate all elements
Iterator<Map.Entry<String, String>> iterator = map.entrySet().iterator(); 
while (iterator.hasNext()) { 
	Map.Entry<String, String> entry = iterator.next(); 
	String key = entry.getKey(); 
	String value = entry.getValue(); 
	System.out.println("Key=" + key + ", Value=" + value); 
}
// 



```
* String
```java
// Decalring a string
String sampleStr = "boka";
// Getting a character at a index
sampleStr.charAt(i);
// initialising a string of size N with '0' character
char carr[] = new char[N];
Arrays.fill(carr, '0');
retString = new String(carr);
// replace a character/sub string from a string
sampleStr.replace("bo","da");
// spliting a string
sampleStr.split("/",0);
// Equality sheck
str1.equals(str2);


```
* Set
```java
// Declaring a Set
Set<Obj> set = new HashSet<Obj> ();
// adding an element
set.add(element)
// removing an element
set.remove(element)
// Checking whether a set contains an element
set.contains(element)
// Clearing a collection - delete all objects
set.clear()
// Size of the set
set.size()

```
* Common tricks
```java
// Character to ASCII 
int chASCII = 'a';
// ASCII to int
char c=(char)chASCII;
// Integer to string
int i = 1234;
String str = Integer.toString(i);
// String to Integer
int i = Integer.parseInt("200");
// List of string to string
String str = String.join(",", strArr);
// Switch case
 switch(expression){    
 case value1:    
  //code to be executed;    
  break;  //optional  
 case value2:    
  //code to be executed;    
  break;  //optional  
 ......    

 default:     
   code to be executed if all cases are not matched;  
```

```
```

```java
https://www.javatpoint.com/java-tuple
```
* Java matrix
```java
// declare empty matrix
int[][] matrix1 = new int[2][2];
int matrix2[][] = new int[2][3];
// Declare matrix with values
String[][] matrix5 = { 
	{ "a", "lion", "meo" }, 
	{ "jaguar", "hunt" } 
};
// getting # rows and # columns
int[][] matrix = {{1,2},{3,4},{5,6}}
int numRows = matrix.length;
int numCOls = matrix[0].length;
```
* General patterns
	* Sorting an array of Java object based on one of its  attribute
	```java
	import java.util.Arrays;
	import java.util.Comparator;

	class SortArrayOfArray{
		public static void sortFunc( int[][] arrayOfArray ){
			if ( arrayOfArray.length == 0 )
				return ;
			Arrays.sort( arrayOfArray , new Comparator<int[]>() {
				public int compare(int[] arr1 , int[] arr2){
					return arr1[0] - arr2[0];
				}
			});
		}
	}



	```
* Stack
```java
// Declare a Stack
Stack<Integer> stack = new Stack<Integer>();
stack.push(elem);
stack.pop(elem);
stack.peek(); // Returns the top element
stack.empty(); // Checks whether a stack is empty or not
```