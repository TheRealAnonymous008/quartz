* A **B-Tree** is a balanced search [[Trees|tree]] designed to work on external memory. They minimize the number of [[Models of Computation|I/O operations]]. 
  
  More specifically it is a rooted tree of minimum degree $m\ge 2$ where
	* Every node has at most $2m$ children. A node is full if it has exactly this amount.
	* Every node except for the root and the leaves, has at least $m-1$ children.
	* The root node has at least two children unless it is a leaf.
	* All leaves appear on the same level at the tree height $h$.
	* A non-leaf node with $k$ children contains $k-1$ keys sorted in non-decreasing order.
	* The keys of a node denoted $x.\text{key}$ separate the ranges of keys stored in each subtree. If $k_i$ is any key stored in the subtree with root $x.c_i$ then 
	  
	  $$
	  k_1 \le x.\text{key}_1 \le k_2 \le x.\text{key}_2 \le \dots \le x.\text{key}_{x.n} \le k_{x.n+1}
	  $$

* B-Trees have a large branching factor compared to [[Binary Search Tree|BSTs]]. However, we can guarantee that every B-Tree has height $O(\lg n)$. 
* For B-Trees we assume that $n$ is so large that it cannot fit into memory at once. Any B-Tree algorithms keep only a constant number of pages in memory at any given time. 

* Disk operations for B-trees are performed as follows. Let $x$ be a pointer to an object.
	* If $x$ is in main memory, we can immediately access them as usual.
	* If $x$ is not in main memory, then we must read the object into main memory before we can refer to its attributes. 
	* Any changes to $x$ require us to perform a disk write operation 
	* Any pages in memory no longer in use are flushed. 

* (*CLRS 18.1*) If $n \ge  1$ then for any $n$-key B-tree $T$ of height $h$ and minimum degree $m\ge 2$, 
  $$
  h\le \log_m \frac{n+1}{2}
  $$
	* B-trees save a factor of $\log_m$ compared to a standard Red-Black tree.

# Operations
* `SEARCH` is a generalization to the search done in a BST except with $n$-way decisions. The ordering of the keys helps with searching.
* `INSERT` involves inserting new keys into existing leaf nodes. If the leaf node $x$ is full, we split the keys of $x$ at the median key into two nodes with only $t-1$ keys each. The median key then moves into $x$'s parent. If the parent becomes full, we repeat this process. 
* `SPLIT` can be done in one pass by splitting any full nodes that we encounter while we traverse the tree.
	* *Splitting is the only way a B-tree increases in height*

![[B Tree Split.png]]
<figcaption> B Tree Split. Image taken from CLRS</figcaption>

* `DELETE` involves not only removing a key from a node in the tree but also re-arranging the keys to preserve the B-Tree property.
	* If the key $k$ is in a leaf node, delete the key from $x$. 
	* If the key $k$ is in an internal node $x$, the do the following
		* If the child $y$ that precedes $k$ in node $x$ has at least $m$ keys, find the predecessor $k'$ of $k$ in the subtree rooted at $y$. Recursively delete $k'$ and replace $k$ by $k'$ in $x$.
		* If $y$ has fewer than $m$ keys then symmetrically examine the child $z$ that follows $k$ in node $x$. If $z$ has at least $t$ keys then find the successor  $k'$ of $k$ in the subtree rooted at $z$. Recursively delete $k'$ and replace $k$ by $k'$ in $x$.
		* If $y$ and $z$ both have $m-1$ keys, merge $k$ and all of $z$ into $y$ so that $x$ loses both $k$ and the pointer to $z$. $y$ now has $2m-1$ keys. Free $z$ and recursively delete $k$ from $y$.
	* If $k$ is not present, determine the root $x.c_i$ of the appropriate subtree that must contain $k$. If $x.c_i$ has only $m-1$ keys, execute these steps. 
		* If $x.c_i$ has only $m-1$ keys but has an immediate sibling with at least $m$ keys, give $x.c_i$ an extra key by moving a key from $x$ to $x.c_i$, moving a key from $x.c_i$'s immediate left or right sibling up into $x$ and moving the appropriate child pointer from the sibling into $x.c_i$.
		* If $x.c_i$ and both siblings have $m-1$ keys, merge $x.c_i$ with one sibling. Move a key from $x$ to the new merged node to become the median key for that note

![[B Tree Deletion Case 1,2.png]]
<figcaption> B Tree Deletion Case 1, 2. Image taken from CLRS</figcaption>
![[Pasted image 20240620135440.png]]
<figcaption> B Tree Deletion Case 3. Image taken from CLRS </figcaption>
# Extensions
* A **B$^+$-tree** extends a B-tree by storing only keys and child pointers in the internal nodes. Any auxiliary information is kept in disk and referred to with these pointer.

# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]] - Ch. 18