* To some extent, all data structures are just graphs in some manner with additional constraints and invariants.
# Set-Based
* [[Set Theory|Set]] based data structures are usually represented with a list of items. Generally, these data structures support the following operations which either query or modify the list. 
	* `SEARCH(S, k)` - given a set $S$ and key value $k$, return a pointer $x$ to an element in $S$ such that `x.key == k` or `NULL`  if no such element exists.
	* `INSERT(S, x)` - augment the set $S$ with the element pointed to by $x$.
	* `DELETE(S, x)` - given a pointer $x$ to an element in $S$, remove $x$ from $S$.
	* `MINIMUM(S)` - assuming a totally ordered set $S$, return a pointer to the element in $S$ with the smallest key.
	* `MAXIMUM(S)` - assuming a totally ordered set $S$, return a pointer to the element in $S$ with the largest key.
	* `SUCCESSOR(S, x)` - assuming a totally ordered set $S$, return a pointer to the next larger element in $S$ or `NIL` if $x=\max S$ 
	* `PREDECESSOR(S, x)` - assuming a totally ordered set $S$, return a pointer to the next smaller element in $S$ or `NIL` if $x=\min S$ 

## Stack, Queue, and Deque
* In a **stack**, we follow a **Last In First Out** policy. The first element deleted is the last element to be inserted.
	* We refer to insertion as **push** and deletion as **pop**.
	* A stack **underflows** if we try to pop an empty stack.
	* A stack **overflows** if we exceed the maximum capacity of the stack $n$ (if any exist)

* In a **queue**, we follow a **First In First Out** policy. The first element deleted is the first element inserted.
	* We refer to insertion as **enqueue** and deletion as **dequeue**
	* When we enqueue an element, it becomes the **tail** of the queue.
	* When we dequeue the queue, we remove the **head** of the queue and replace it with its successor.

* A **deque** is a double ended queue where we allow insertion and deletion on both ends of the list. 

## Linked List
* A **linked list** is a data structure where objects are arranged in a linear order where an item points (via pointer) to the next item on the list.
* A **doubly linked list** extends the linked list to allow items to point to the previous item as well. 
* A **circular list** extends a linked list by linking the tail to the head. 
* We can add a **sentinel** -- a dummy object that simplifies boundary conditions (i.e., when dealing with the predecessor of the head and the successor of the tail). 
	* By doing this, we create a "circular list". 

## Flattened Lists
* A **flattened list** is an umbrella term for a data structure that is usually represented with pointers, but is instead represented as an ordered list of items.
* We use this structure if pointers and objects are unavailable to us.
* Sometimes, this creates the effect of simulating how the computer [[Operating System|operates on memory]] -- including allocation, deletion, and garbage collection 

## Specialized Lists
* A **suffix array** is a sorted array of all the suffixes of a string. They can be seen as a space efficient alternative to [[Trie#Suffix Trees|Suffix Trees]]
  
  Let $S=S[1]S[2]\dots S[n]$ be an $n$-string and $S[i,j]$ the substring ranging from $i$ to $j$ inclusive.
  
  The suffix array $A$ of $S$ is the array of integers providing the starting positions of suffixes of $S$ in lexicographic order. That is $i$ contains the starting position of the $i$-th smallest suffix of $S$.
  
  $$
  \forall 1\le i \le n \ , S[A[i-1],n] < S[A[i],n]
  $$
	* A suffix array can be constructed using DFS on a suffix tree assuming edges are visited in lexicographic order. 
	* A suffix array requires $O(n\log n)$ space, whereas the original text only requires $O(n\log \sigma)$ where $\sigma$ is the size of the alphabet. 

## [[Hashed Data Structure]]

# Graph-Based
* [[Graph Theory|Graphs]]
	* [[Trails, Walks, Paths and Cycles]]
* Tree-based:
	* [[Binary Search Tree]]
	* [[Trie]]

# Augmented
* In general, data structures can be augmented beyond their original use case if their structure and operations can help solve another problem with more data.
  
  Augmenting follows these general steps
	* Choose a data structure
	* Determine additional information to maintain in the underlying data structure
	* Verify that we can maintain the additional information for the basic modifying operations on the underlying data structure. 
	* Develop new operations.

* While the steps are outlined above, it is important to note that designing may not follow these steps. 
# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|Cormen, Leiserson, Rivest, and Stein]] - Part III.
* [[Algorithms]]