## Artifact 1: Analyzing Recursive Algorithms With Backwards Substitution

```pseudocode
ALGORITHM SumEvens(arr):  
	// Sums up all even elements in an array.  
	// input: arr is an array of numbers  
	// output: the sum of all even numbers in the array
	
	if (arr.length == 0): // checks for bad input return 0
  	n = arr.length  
  	sum = 0  
  	if arr[n-1] % 2 == 0:	
  	sum = arr[n-1]
  	if (n == 1): // base case	
  		return sum  
  	else:  	
  		return sum + SumEvens(arr[0...n-2])
```

### Steps:

1. Decide on the parameters that indicate the input’s size.

   * The size of the input is typically dependent on the size of the data being passed into the algorithm, and there can be more than one parameter that affects the input’s size
   * Look at the input parameters and determine which ones are being affected by the algorithm.
   * In the example above, the input size is the length of the array since each of its elements are being affected when the algorithm runs.

2. Identify the basic operation of the algorithm

   * The basic operation of an algorithm is the line of code that does the main work of the algorithm.
   * It can be an assignment, comparison, arithmetic operation, etc.
   * In the example, the main work of the algorithm is checking whether a particular element of the array is even; therefore, the basic operation is `if arr[n-1] % 2 == 0:`.

3. Check whether the number of times the basic operation is executed differs on inputs of the same size.

   * Look for exit cases and places where the data is modified that might result in differing numbers of operations for unique input data of the same size.
   * This enables one to determine the best, average, and worst cases for the algorithm's time complexity.
   * In the example, the algorithm passes over each element of the array without running into exit cases or modifying its contents, so the algorithm will have the same number of operations for arrays of the same length.
   
4. Set up the recurrence relation

   * The recurrence relation models the number of basic operations for a given input size n.
   * In recursive algorithms, the number of basic operations depends heavily on the number of times the algorithm must repeat over the input before reaching the base case which specifies the bottom of the algorithm's stack and is not dependent on other recursive calls.
   * The following is the recurrence relation of the example algorithm where F(n) is the number of basic operations and n is the input size:
   * F(n) = F(n-1) + 1
     * F(n-1) represents each algorithm call over the input.
     * 1 represents the basic operation that occurs during each run.
   * F(1) = 1
     * This is our base condition represented by the algortihms base case. When the input size is one, the algorithm will execute the basic operation one time.
     * When this base case is reached, no more calls to the algorithm will occur.

5. Solve the recurrence relation

   * To solve the recurrence relation, substitute F(n-1) for its functional equivalent.
     * F(n) = F(n - 1) + 1
     * Since F(n - 1) = F(n - 2) + 1, F(n) = (F(n - 2) + 1) + 1
   * Repeat these substitutions to establish a general pattern with variables instead of number in the function parameter.
     * F(n) = ((F(n - 3) + 1) + 1) + 1
     * F(n) = F(n - 3) + 3
  * F(n) = F(n - i) + i
   * Determine a value for the variable that achieves the recurrence relation's base case.
     * Let i = n - 1
     * F(n) = F(n - (n - 1)) + (n - 1)
     * F(n) = F(1) + n - 1
   * Substitute the result of the base case into your relation and solve for F(n).
     * F(n) = 1 + n - 1 = n
     * F(n) = n
   * Convert the result of the solved recurrence relation to its asymptotic time complexity by stripping all lower-order terms, scalar multiples, and constants.
     * F(n) = n
     * The asymptotic time complexity of the recursive algorithm is O(n).
