### Pseudocode Convention Practice

```pseudocode
LINEAR-SEARCH(A,n,x)
found = false
i = 1
while found ≠ true and i <= n
	if A[i] = x
		found = true
	else
		i ++
if found = true
	return i
else
	return 0
```


#### Find Max Element

```pseudocode
FIND-MAX(A,n)
m = 0
for i = 1 to n
	if A[n] > m
		m = A[n]
return m
```


### Dynamic Set Operations

Dynamic set operations:

-   SEARCH (S, k) - returns a pointer to k (key)
-   INSERT (S, x) - augments S with x
-   DELETE (S, x) - removes x
-   MINIMUM (S) - returns element of S with smallest key
-   MAXIMUM (S) 
-   SUCCESSOR (S, x) - returns pointer to the next largest element or NIL if x is the maximum
-   PREDECESSOR (S, x) - next smallest element to x or NIL


### Stacks

LIFO structure
Insert / Delete = push / pop (like a spring loaded stack of plates)


![[Pasted image 20230125223702.png]]


Poping an empty stack = **underflow**
If S.top exceeds  _n_ = **overflow**

```pseudocode
PUSH(S,x)
	S.top = s.top + 1
	S[S.top] = x
```

```pseudocode
POP(S)
	if S.top = 0
		error "underflow"
	else
		x = S[S.top]
		S.top = S.top - 1
		return x	
```

```pseudocode
STACK-EMPTY(S)
	if S.top == 0
		return true
	else
		return false
```


#### Discussion

I guess the real-life scenario of a stack would be my drive at home that it only one car wide and we have two cars? Whoever is out first in the morning needs to be in position _S.top_. As you note Felipe undo stacks seem to be a common computing application of stacks or maybe the back button on a browser.

I like the example of parentheses tracking by compilers - I always considered the work of compilers to be way too complex to begin to understand so it's nice to see a simple data strcuture being used.

### Queues

**FIFO** structure
has a **head** and a **tail**

Items added at the tail, removed from the head

```pseudocode
ENQUEUE(S,x)
	if Q.head == Q.tail - 1 then
		// overflow
	else
		Q.[Q.tail] = x
		if Q.tail == Q.length 
			Q.tail = 1
		else
			Q.tail = Q.tail + 1
```

```pseudocode
DEQUEUE(S)
	if Q.head == Q.tail then
		// underflow
	else
		x = Q[Q.head]
		if Q.head == Q.length then
			Q.head = 1
		else
			Q.head = Q.head + 1
```

#### Activity 

```pseudocode
FRONT(Q)
	if Q.head = Q.tail then
		error - queue is empty
	else
		return Q[Q.head]
```



### Linked Lists

**HEAD** is the _**start**_ of the list - **POINTER ONLY**

```pseudocode
LIST-SEARCH(k)
	i = L.head
	while i is not NULL
		if i.data == k
			return L[i]
		i = i.next
	return NULL
```

```pseudocode
LIST-INSERT(x)
	x.next = L.head
	L.head.prev = x
	L.head = x
```

```pseudocode
LIST-DELETE(x)
	if x.prev is NULL
		x.next.prev = NULL
	else
		x.next.prev = x.prev
	if x.next is NULL
		x.next.next = NULL
		L.head = x
	else
		x.next.next = x.next
```

#### Activity 
##### Exercise one
 >Write the pseudo-code for the dynamic-set operation INSERT on a singly linked list in **_O_** (1) time? How about DELETE?


```pseudocode
INSERT(x)
	x.next = L.head
	L.head = x.key
	
DELETE() //deletes the first element
	L.head = L[L.head].next
	
	
```

##### Exercise two
> Implement a stack using a singly linked list L. Write the pseudo-code for the operations PUSH and POP in **_O_** (1) time. You can play with the algorithm simulation software to see how it works: [https://www.cs.usfca.edu/~galles/visualization/StackLL.html Links to an external site.](https://www.cs.usfca.edu/~galles/visualization/StackLL.html).
```pseudocode 
PUSH(x)
	x.next = L.head     //set next pointer of new item to current head
	L.head = x.index      //set head to new item

POP()
	print L[L.head].data     //output the top of the stack
	L.head = L[L.head].next  // update the next pointer to omit item at head

PEEK()
	print L[L.head].data     //output the top of the stack

```

##### Exercise three
> Implement a queue by a singly linked list L. Write the pseudo-code for the operations ENQUEUE and DEQUEUE in **_O_** (1) time. You can play with the algorithm simulation software to see how it works: [https://www.cs.usfca.edu/~galles/visualization/QueueLL.html Links to an external site.](https://www.cs.usfca.edu/~galles/visualization/QueueLL.html).

```pseudocode
ENQUEUE(x)
	L[L.length].next = x
	
DEQUEUE()
	x.next = L.head     //set next pointer of new item to current head
	L.head = x.index      //set head to new item
```

##### Exercise four (challenge)
>As written, each loop iteration in the LIST-SEARCH’ procedure (in Algorithms textbook p.239) requires two tests: one for x ≠ L.nil and one for x.key ≠ k. Show how to eliminate the test for x ≠ L.nil in each iteration.

```pseudocode

```