# Binary Search Tree
* A **binary search tree** is a binary tree organized to satisfy the binary-search tree property:
  
  Let $x$ be a node in a binary search tree. If $y$ is a node in the left subtree of $x$, then $y.\text{key} \le x.\text{key}$. If $y$ is a node in the right subtree of $x$, then $y.\text{key} \ge x.\text{key}$ 
* By convention, all leaves have `NIL` values.

## Operations
* Traversal across the tree takes $\Theta(n)$ time. 
	* The binary search tree property allows us to print all keys in sorted order. This is called **inorder traversal**
	```
	if x != null
		INORDER(x.left)
		print(x.key)
		INORDER(x.right)
	```
	* We can also print the root before the values in either subtree. This is **preorder traversal**
	```
	if x != null
		print(x.key)
		PREORDER(x.left)
		PREORDER(x.right)
	```
	* We can also print the root after the values in either subtree. This is **postorder traversal**
	```
	if x != null
		PREORDER(x.left)
		PREORDER(x.right)
		print(x.key)
	```

* A binary search tree is often used to perform `SEARCH`operations. Search can be done in $O(h)$ time where $h$ is the height of the tree. Extensions of search are also $O(h)$ time.
	* The `MINIMUM` of the tree is the left most node.
	* The `MAXIMUM` of the tree is the right most node.
	* The `SUCCESSOR` of a node $x$ is given as follows: 
		* If the right subtree of $x$ is not empty, the successor is the leftmost node in $x$'s right subtree.
		* If the right subtree of $x$ is empty and $x$ has a successor, then $y$ is the lowest ancestor of $x$ whose left child is also an ancestor of $x$
	* The `PREDECESSOR` of a node $x$ is given as follows.
		* If the left subtree of $x$ is not empty, the predecessor is the rightmost node in $x$'s left subtree.
		* If the left subtree of $x$ is empty and $x$ has a predecessor, then $y$ is the lowest ancestor of $x$ whose right child is also an ancestor of $x$.

* `INSERT` is given by inserting a new node $z$ in the tree such that the binary search property is maintained. Insert takes $\Theta(h)$
	* To find where to place $z$ we simply perform a traversal until we reach a leaf $v$ and then insert $z$ either to the left or to the right of $v$ depending on the values of their keys. 
	* If $z$ is the first node to be inserted in the tree, $z$ also becomes the root.

* `DELETE` for node $z$ in Binary Search Tree $T$ must handle three cases. Delete takes $\Theta(h)$
	* If $z$ has no children, simply remove it from the tree. Modify the parent accordingly.
	* If $z$ has one child, elevate that child to take $z$'s position in the tree by doing `z.parent.child = z.child`, where child is left if `z.child` was a left child and right otherwise. 
	* If $z$ has two children, first find $z$'s successor $y$. $y$ must lie in $z$'s right subtree and must have no left children. Splice $y$ out of its current location and have it replace $z$.
		* If $y$ is $z$'s right child, replace $z$ by $y$. 
		* If $y$ is not $z$'s right child, replace $y$ by its own right child and then replace $z$ by $y$.
![[BST Deletion.png]]
<figcaption> BST Deletion. Image taken from CLRS </figcaption>


* **Rotation** is a local operation that preserves the Binary Search Tree property but changes the pointer structure
	* `LEFT ROTATION(x)`: Suppose $x$ is any node such that its right child $y$ is not `NULL`.  We pivot around the link from $x$ to $y$ so that $y$ is the new root of the subtree, with $x$ as $y$'s left child, and $y$'s left child as $x$'s right child.
	* `RIGHT ROTATION(x):`Suppose $y$ is any node such that its left child $x$ is not `NULL`. We pivot around the link from $y$ to $x$ so that $x$ is the new root of the subtree, with $y$ as $x$'s right child and $x$'s right child as $y$'s left child. 
![[BST Tree Rotation.png]]
<figcaption> Tree Rotation. Image taken from CLRS  </figcaption>

## Properties
* *Assuming a balanced binary search tree, the height $h$ is $O(\log n)$*. 

* (*CLRS 12.4*) The expected height of a randomly built binary search tree on $n$ distinct keys is $O(\lg n)$.  [^BST_1]

[^BST_1]: The proof for this relies on [[Mathematics|Jensen's Inequality]]. 

# Red-Black Trees
* A **red-black tree** is a binary search tree with one extra bit of storage per node for the node's color.  In particular
	* Every node is either red or black
	* Every leaf has `NIL`and is black
	* If a node is red, then both its children are black
	* For each node, all simple paths from the node to descendant leaves contain the same number of black nodes. 

* *A red-black tree ensures no path from the root to a leaf is twice as long as any other so that the tree is approximately balanced*. 

* (*CLRS 13.1*) A red black tree with $n$ internal nodes has height at most $2 \lg (n+1)$. 
	* An immediate consequence of this is that any BST operation that takes $\Theta(h)$ time takes $\Theta(\lg n)$ time.

## Operations
* The regular `INSERT` and `DELETE` operations in BST cannot be directly adapted to Red-Black Trees because any such operations may break the red-black property. 

### Insert
* During `INSERT` of node $z$, we set its color to be red. We then fix the tree since it may violate the Red-Black property. This still takes $O(\lg n)$ time. 
* We maintain the following invariants:
	* The variable $N$ representing the current node $N$, initially the inserted node, is made variable running through the loop
	* $N$ is red at the beginning of each iteration.
	* All red nodes do not have red children except for possibly $N$ and its parent $P$.
	* All other properties are satisfied throughout the tree.

* *Case 1*: $N$'s parent is black. In which case we do not need to do anything.  

* *Case 2*: Both $P$ and the uncle $U$ are red. In which case we can repaint them black and the grandparent $G$ becomes red. 
  
  Since $G$ may now induce a red-red violation, we do $N\gets G$. 
![[RB Tree I2.png]]
<figcaption> Red Black Insert Case 2. Image taken from CLRS.</figcaption>

* *Case 3*: The total height of the tree has increased by $1$. The current node $N$ is the red root of the tree.

* *Case 4*: $P$ is red and the root. Switch $P$'s color 

* *Case 5*: $P$ is red but the uncle $U$ is black.  $N$ is either $G.\text{left.right}$ or $G.\text{right.left}$.  Rotate $P$ to the grandparent position and proceed to Case 6 with $N\gets P$

* *Case 6*: $N$ is the left-left child or right-right child of $G$. Let `dir` be either left if $N$ is left-left and right otherwise. Perform a rotation in the opposite direction at $G$ such that
  
  $P$ is in $G$'s position
  $P$ is the parent of $N$ and $G$.
![[RB Tree I5-6.png]]
<figcaption> Red Black Insert Case I5 and I6. Image taken from CLRS </figcaption>

## Delete
* We cannot use the `DELETE` procedure of a regular Binary Search Tree since we may violate the Red-Black property.  The overall run time for this procedure is $O(\lg n)$. 

* We consider, first, the simple cases. Let $N$ be the deleted node.
	* If $N$ has 2 children, swap its value with the in-order successor and then delete the successor instead. 
	* If $N$ has $1$ child, replace the node with its child and color it black. 
	* If $N$ has no children and is the root, replace it with `NULL`.
	* If $N$ has no children and is red, remove the leaf node.
	* If $N$ has no children and is black, remove it but make sure to fix the tree to rebalance it. 

* When rebalancing the tree, we maintain the following invariants
	* At the beginning of each iteration, the black height of $N$ equals the iteration number minus one. 
	* The number of black nodes on the paths through $N$ is one less than before the deletion, whereas it is unchanged on all other paths. There is a black-violation at $P$ if other paths exist.
	* All other properties are satisfied throughout the tree

* *Case 1*: $N$ is the new root. The black height decreases by $1$ and we do not need to do anything else.

* *Case 2*: $P, S$ and $S$'s children are black. Paint $S$ red and $N\gets P$ since we may violate the red-black property. We rebalance one black level higher.

* *Case 3*: The `dir`-sibling $S$ is red and so $P$ and nephews $C,D$ have to be black.  Perform a `dir`-rotation at $P$ so that $S$ becomes $N$'s grandparent and reverse the colors of $P$ and $S$ then proceed to Cases 4, 5, 6. 

* *Case 4*; $S$ and $S$'s children are black but $P$ is red. Change the colors of $S$ and $P$ to be red and black respectively. This makes up for our deleted black node.

* *Case 5* :  `dir`-sibling $S$ is black. $S$'s close child $C$ is red and $S$'s distant child $D$ is black. Do a `(1-dir)`-rotation at $S$ so that $C$ becomes $S$'s parent and $N$'s new sibling.
  
  Exchange the colors of $S$ and $C$. $N$ has a black sibling whose distant child is red so we proceed to Case 6.

* *Case 6* : `dir`-sibling $S$ is black, $S$' distant child $D$ is red. Do a `dir`-rotation at $P$ so that $S$ becomes the parent of $P$ and $D$. Exchange the colors of $P$ and $S$ and make $D$ black.
  
  Paths not passing through $N$ pass through the same number of black nodes
  
  $N$ has one additional black ancestor so the path passing through $N$ pass through one additional black node.


![[RB Delete.png]]
<figcaption> Red Black Delete Fixup. Image taken from CLRS.  In the above, Case 1 = Case D3; Case 2 =Case D4; Case 3 = Case D5; Case 4 = Case D6 </figcaption>

* (*CLRS 14.1*). Red black trees can be augmented.
  
  Let $f$ be an attribute that augments a red-black tree $T$ of $n$ nodes and suppose that the value of $f$ for each node $x$ only depends on the information in nodes `x` `x.left` and `x.right`, possibly including `x.left.f` and `x.right.f`. Then, we can maintain the values of $f$ in all nodes of $T$ during insertion and deletion without asymptotically affecting the $O(\lg n)$ performance of these operations
  
  *Intuition*: Any change to $f$ only propagates to the $O(\lg n)$ ancestors of a node. 


# Order Statistic Trees 
* An **order statistic tree** is a red-black tree with additional information. Each node stores a "size" attributed. The **size** contains the number of internal nodes in the subtree rooted at $x$ including $x$ itself.
* To retrieve the rank of any element in the tree, we do the following
  
  First calculate the rank of $x$ in the subtree it is rooted in. This is given as the size of its left subtree + 1 (to include itself). If the input rank $i$ is also equal to its rank $r$ in the subtree we are done
  
  Otherwise, traverse the left subtree with call `SELECT(x.left, i)` if $i<r$. This follows because we know the targeted node is to the left by the Binary Search property
  
  Otherwise, if $i>r$ traverse the right subtree with call `SELECT(x.right, i - r)`. Here, we know that the node must lie to the right and we "prune" out the other nodes and only consider the current subtree. This prunes out $r$ nodes hence our adjusted rank is $i-r$.


* To maintain the subtree sizes during insertion and deletion, we simply increment or decrement the sizes of all affected parent / children nodes. This takes $O(\lg n)$ time. 
  
  When we adjust the tree with rotation, at most two nodes are affected. We adjust the sizes of these nodes accordingly. 

# Interval Trees
* An **interval** is defined using a pair of real numbers $t_1, t_2$. $t_1$ is called the low endpoint and $t_2$ the high endpoint. 
  
  Intervals $i,i'$ overlap if $i\cap i'\ne \emptyset$.
* Any two intervals satisfy the **interval trichotomy**. Exactly one of the following must be true
	* $i,i'$ overlap
	* $i$ is to the left of $i$'
	* $i$ is to the right of $i$'

* An **interval tree** is a red-black tree where each element contains an interval. New intervals can be inserted, deleted or queried. 
  
  To facilitate better search operations, we maintain for each node `x` the value `x.max` which denotes the maximum value of any interval endpoint stored in the subtree rooted at $x$.
  
  `x.max` is maintained via the following relation
  ```
  x.max = max(x.int.high, x.left.max, x.right.max)
  ```


* In order to search for an interval that overlaps $i$, we do the following

![[Interval Tree Search.png]]
<figcaption> Interval Tree Search. Image taken from CLRS </figcaption>


* (*CLRS 14.2*) Any execution of `INTERVAL-SEARCH(T,i)` above either returns a node whose interval overlaps $i$ or returns `NULL` if no such interval exists.
  
  *Proof Idea*: We use the invariant that if tree $T$ contains an interval that overlaps $i$, then the subtree rooted at $x$ contains such an interval.
# Links
* [[Trees]]
* [[Labelled Trees]]
* [[Spanning Trees and Forests]]

* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]] - Ch. 12, 13, 14