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

## Disjoint Set Operations
* A **disjoint set data structure** maintains a collection $\mathcal{S}= \{S_1,\dots, S_k\}$ of disjoint dynamic sets. Each set is identified by a representative, some member of the set. 
* It supports the following operations
	* `MAKE_SET(x)` - create a new set whose only member is $x$, where $x$ is not in some other dataset
	* `UNION(x,y)` - unites the dynamic sets that contain $x$ and $y$ into a new set that is the union of these two sets. We then destroy the input sets.
	* `FIND_SET(x)` - returns a pointer to the representative of the unique set containing $x$.

* One way to represent disjoint sets is through a linked list.  Each set corresponds to one linked list with a `head` and `tail`. All elements in the set are connected to the set's `head`. 
	*  `MAKE_SET` and `FIND_SET` take $O(1)$ time. `FIND_SET` can be done by outputting the head of the set. 
	* For `UNION` we can consider using the **weighted union heuristic** where we *append the shorter list into the longer list*. 
	* (*CLRS 21.1*) Using the linked list representation of disjoint sets, a sequence of $m$ `MAKE_SET`, `UNION` and `FIND_SET` operations $n$ of which are `MAKE_SET` operations, takes $O(m + n\lg n)$ time. 
		* This follows because each object's pointer is updated at most $\lg n$ times over all `UNION` operations

* Another possible representation is through [[Trees|Rooted trees]] where each node contains one member and each tree represents one set. The root of each tree contains its representative and is its own parent
	* A `UNION` operation causes the root of one tree to point to the root of another.
	* `FIND_SET` traverses the tree until we reach the root of the tree. 
	* We can use the following heuristics:
		* The **union by rank heuristic** involves *making the root of the tree with fewer nodes point to the tree with more nodes.* Here, we maintain a rank -- an upper bound on the height of the node. 
			* This gives a runtime of $\Theta(m\lg n)$ with $n$ `MAKE_SET` and $m$ total operations.
			* This introduces a `LINK` operation that performs the union by rank heuristic
		* The **path compression** heuristic involves using each node on a path point directly to the root. 
			* Here, we make two passes whenever we do `FIND_SET`. The first is to find the node, and the second is to update each node to point to the root directly
			* For a sequence of $n$ `MAKE_SET` and $f$ `FIND_SET` operations, this gives a worst case running time of $\Theta(n + f\cdot (1 + \log_{2+f/n} n)$
		* (*CLRS 21.14*) A sequence of $m$ `MAKE_SET`, `UNION`, and `FIND_SET` operations $n$ of which are `MAKE_SET` can be performed on a disjoint forest with union by rank and path compression in worst-case  $O(m\alpha (n))$ where $\alpha(n)$ is the Ackermann function .
			* (*CLRS 21.11*) - the amortized cost of each `MAKE_SET` operation is $O(1)$
			* (*CLRS 21.12*) - the amortized cost of each `LINK` operation is $O(\alpha (n))$ 
			* (*CLRS 21.13*) - the amortized cost of each `FIND_SET` operation is $O(\alpha(n))$ 
# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]] 