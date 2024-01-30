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
