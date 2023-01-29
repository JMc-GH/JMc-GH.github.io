
### Why is sorting fundamental

Application functionality requires it
Use soritng as a subroutine to e.g. sort graphical layers
Development of sorting algorithms is of historial interest as inportant techniques often appear in sort algorithms
Because there is a provable minimum time (based on lower bound) - fastest sorts are the ones that are closest to this minimum time.
Accounting for situational differences can be achieved at alogorithmic level rather than attempting to performance tune code.

### Sorting Algorithms

**sorting in-place** -A new data structure is not needed to perform the sort, so no extra memory is allocated. Useful when memory space is limited.

**Insert sort** - sorts _in-place_ with _tight inner loop_ (only performs a simple operation) - complexity is O(n2) - i.e. not great

**Merge Sort** - better O(n log n) but does not sort _in-place_

**Heatsort** - sorts _in-place_ with performance of O(n log n) - uses a **heap** data structure 

**Quicksort** - sorts _in-place_ performance of worst case O(n2) but expected running time is O(n log n) - tight code, running time is small

![[Pasted image 20230129133557.png]]



