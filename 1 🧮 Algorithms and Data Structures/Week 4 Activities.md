This is the pseudocode I came up with for the linear search in 4.1; its different to the answer given - but does the same thing (I think). Does it matter that the code is different?

```
LINEAR-SEARCH(A,n,x)found = falsei = 1while found ≠ true and i <= n    if A[i] = x        found = true    else        i ++if found = true    return ielse    return 0
```

For activity 1 I came up with this:

`FIND-MAX(A,n)`  
`m = 0`  
`for i = 1 to n`  
    `if A[n] > m`  
        `m = A[n]`  
`return m   `  
  
I think that this has a time complexity of O(n) as it is required to iterate every element in the array - like the linear search (worst case). But, I'm starting to worry that I've reached of my capacity to understand time complexity...