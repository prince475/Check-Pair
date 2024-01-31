# DSA ONE

## Check if pair with given Sum exists in Array (Two Sum)

Given an array [] of n numbers and another number x, the task is to check whether or not there exists two elements in A[] whose is Exactly x.

```text
    Input: arr[] = { 0, -1, 2, -3, 1 }, x = -2
    Output: Yes
    Explanation: If we calculate the sum of the output, 1 + (-3) = -2
```

```text
    Input: arr[] = { 1, -2, 1, 0, 5 }, x = 0
    Output: No
```

## Approach 1 (Basic Approach)

- Traverse the array using a loop
- For each element
  - Check if there exist another in the array with sum as x
  - Return true if yes, else continue
- If no such pair exists, return false

```js
    // Javascript program to check if there exists a pair
    // in array whose sum results in x

    // Function to find and print pair 
    function findPair(a, size, x) {

        for (i=0; i < (size-1); i++){
            for (j = (i + 1); j < size; j++) {
                if (a[i] + a[j] === x) {
                    document.write("Pair with a given sum"+x+"is ("+a[i]+", "+a[j]+")");

                    return true;
                }
            }
        }

        return false;

        let a = [0, -1, 2, -3, 1];
        let x = -2;
        let size = a.length;

        if (findPair(a, size, x)) {
            document.write("<br/> Valid Pair exists");
        } else{
            document.write("<br/>No Valid Pair exists for" + x);
        }
    }
```
## Time Complexity

Time Complexity: O(N^2), Finding pair for every element in the array of size N.
Auxiliary Space: O(1)

### Two Sum using Sorting and Two-Pointers technique

```txt
    The idea here is to use the two-pointer technique. In order for us to use the two-pointer technique, the array must be sorted. Once the array is sorted the two pointers can be taken and this marks the beginning and end of the array respectively. If the sum is greater than the sum of those two elements, shift the right pointer to decrease the value of the required sum and if the sum is lesser than the required value, shift the left pointer to increase the value of the required sum.
```

#### Illustration

```txt
    Let an array be {1, 4, 45, 6, 10, -8} and sum to find be 16
    After sorting the array 
    a = {-8, 1, 4, 6, 10, 45}
    Now, increment ‘l’ when the sum of the pair is less than the required sum and decrement ‘r’ when the sum of the pair is more than the required sum. 
    This is because when the sum is less than the required sum then to get the number which could increase the sum of pair, start moving from left to right(also sort the array) thus “l++” and vice versa.
    Initialize l = 0, r = 5 
    A[l] + A[r] ( -8 + 45) > 16 => decrement r. Now r = 4 
    A[l] + A[r] ( -8 + 10) increment l. Now l = 1 
    A[l] + A[r] ( 1 + 10) increment l. Now l = 2 
    A[l] + A[r] ( 4 + 10) increment l. Now l = 3 
    A[l] + A[r] ( 6 + 10) == 16 => Found candidates (return 1)
```

- Note: If there is more than one pair having the given sum then this algorithm reports only one. Can be easily extended for this though. 

### Solving the problem step-wise

- hasArrayTwoCandidates (A[], ar_size, sum)
- Sort the array in non-decreasing order.
- Initialize two index variables to find the candidate elements in the sorted array. 
  - Initialize first to the leftmost index: l = 0
  - Initialize second the rightmost index: r = ar_size-1
-Loop while l < r. 
  - If (A[l] + A[r] == sum) then return 1
  - Else if( A[l] + A[r] < sum ) then l++
  - Else r–
- No candidates in the whole array – return 0

### Code implementation

```js
    // Javascript program to check if given array
    // has 2 elements whose sum is equal
    // to the given value
    
    // Function to check if array has 2 elements
    // whose sum is equal to the given value
    function hasArrayTwoCandidates(A, arr_size, sum) {
        var l, r;
    
        /* Sort the elements */
        A.sort();
    
        /* Now look for the two candidates in the sorted array*/
        l = 0;
        r = arr_size - 1;
        while (l < r) {
            if (A[l] + A[r] == sum)
                return 1;
            else if (A[l] + A[r] < sum)
                l++;
            else // A[i] + A[j] > sum
                r--;
        }
        return 0;
    }
    
    /* Driver program to test above function */
    var A = [ 1, 4, 45, 6, 10, -8 ]
    var n = 16;
    var arr_size = A.length;
    // Function calling
    if (hasArrayTwoCandidates(A, arr_size, n))
        document.write("Array has two elements" +
                " with the given sum");
    else
        document.write("Array doesn't have two" +
                " elements with the given sum");
    
```


