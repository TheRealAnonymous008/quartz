* To some extent, all data structures are just graphs in some manner with additional constraints and invariants.
## Set-Based
* [[Set Theory|Set]] based data structures are usually represented with a list of items. Generally, these data structures support the following operations which either query or modify the list. 
	* `SEARCH(S, k)` - given a set $S$ and key value $k$, return a pointer $x$ to an element in $S$ such that `x.key == k` or `NULL`  if no such element exists.
	* `INSERT(S, x)` - augment the set $S$ with the element pointed to by $x$.
	* `DELETE(S, x)` - given a pointer $x$ to an element in $S$, remove $x$ from $S$.
	* `MINIMUM(S)` - assuming a totally ordered set $S$, return a pointer to the element in $S$ with the smallest key.
	* `MAXIMUM(S)` - assuming a totally ordered set $S$, return a pointer to the element in $S$ with the largest key.
	* `SUCCESSOR(S, x)` - assuming a totally ordered set $S$, return a pointer to the next larger element in $S$ or `NIL` if $x=\max S$ 
	* `PREDECESSOR(S, x)` - assuming a totally ordered set $S$, return a pointer to the next smaller element in $S$ or `NIL` if $x=\min S$ 

### Stack, Queue, and Deque
* In a **stack**, we follow a **Last In First Out** policy. The first element deleted is the last element to be inserted.
	* We refer to insertion as **push** and deletion as **pop**.
	* A stack **underflows** if we try to pop an empty stack.
	* A stack **overflows** if we exceed the maximum capacity of the stack $n$ (if any exist)

* In a **queue**, we follow a **First In First Out** policy. The first element deleted is the first element inserted.
	* We refer to insertion as **enqueue** and deletion as **dequeue**
	* When we enqueue an element, it becomes the **tail** of the queue.
	* When we dequeue the queue, we remove the **head** of the queue and replace it with its successor.

* A **deque** is a double ended queue where we allow insertion and deletion on both ends of the list. 

### Linked List
* A **linked list** is a data structure where objects are arranged in a linear order where an item points (via pointer) to the next item on the list.
* A **doubly linked list** extends the linked list to allow items to point to the previous item as well. 
* A **circular list** extends a linked list by linking the tail to the head. 
* We can add a **sentinel** -- a dummy object that simplifies boundary conditions (i.e., when dealing with the predecessor of the head and the successor of the tail). 
	* By doing this, we create a "circular list". 

### Flattened Lists
* A **flattened list** is an umbrella term for a data structure that is usually represented with pointers, but is instead represented as an ordered list of items.
* We use this structure if pointers and objects are unavailable to us.
* Sometimes, this creates the effect of simulating how the computer [[Operating System|operates on memory]] -- including allocation, deletion, and garbage collection 

### Hashed Data Structures


# Graph-Based
* [[Graph Theory|Graphs]]
	* [[Trees]]
	* [[Trails, Walks, Paths and Cycles]]

## Tree Based

# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|Cormen, Leiserson, Rivest, and Stein]] - Part III.