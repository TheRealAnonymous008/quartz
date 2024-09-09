* A tree is **labelled** if each vertex is distinguished from each other.
* **Cayley's Formula** - The number of labelled trees in $n$ vertices is $n^{n-2}$. 
	* **Pitman's Proof** relies on double counting. There are $n!$ to permute the number of vertices and say $T_n$ spanning trees on $n$vertices.
	  
	  Another way to count is to add the edges one by one. If we have added $n-k$ edges, we have a forest of $k$ trees. So there are $n(k-1)$ ways to choose the next edge (choose the vertex and the tree to join it with). These two count the same thing to get 
	  $$
	  n! T_n = \prod_{k=2}^nn(k-1)= n^{n-1}(n-1)!= n^{n-2}n!
	  $$
	  
	  * **Prufer's proof** establishes a bijection of trees with $n$ vertices and the sequence of $n-2$ vertices.
	    
	    In the forward direction, at each step, choose the leaf with the smallest label, say $x_i$ and the edge $x_iy_i$ until we get two vertices. The sequence is the sequence of $y_i$'s.
	    
	    In the reverse direction, at the $i$-th step, let $x_i$ be the smallest number not in the sequence. JJoin it with the vertex labelled $y_i$. At the last step, join the remaining vertices.

* Prufer's proof gives us the **Prufer Sequence**, a sequence of $n-2$ numbers that specify an $n$-vertex labelled tree.
	* (*Theorem:* $x\notin \{x_1,\dots, x_{n-2}\}$ if and only if $x$ is not a leaf
	  
	  *Proof*: Eventually $v_x$ must be connected to the other vertices at least once.
	   
	   By Prufer's algorithm, it is not connected to any other vertex when it is the smallest number not yet considered that hasn't appeared in the sequence. So, we know that it must never appear in the sequence, otherwise it will be connected more than once, hence it will no longer be a leaf.

	* *Theorem*: The probability that a vertex in a labelled tree is a leaf approaches $\frac{1}{e}$ as $n\to \infty$.
	  
	  *Proof*: Apply the previous theorem and Cayley's Formula. If the given vertex is $x$, then for it to be a leaf in some tree, it must not appear in the Prufer Sequence. There are $(n-1)^{n-2}$ such trees, and by Cayley's Formula, there are $(n)^{n-2}$ trees. So take the limit 
	  $$
	  \begin{equation} 
	  \begin{split}
	  \lim_{n\to\infty} \left(\frac{({n-1})^{n-2}}{n^{n-2}}\right)&= \lim_{n\to\infty} \left(\frac{n-1}{n}\right)^{n-2}  \\
	  &=\lim_{n\to\infty} \left(1-\frac{1}{n}\right)^{n-2}  \\
	  &=\frac{1}{e}
	  \end{split}
	  \end{equation}
	  $$

* (*Wilson e10.7*) - Let $T(n)$ be the number of labelled trees on $n$ vertices. The following identity holds 
  $$
  2(n-1)T(n)=\sum_{k=1}^{n-1}{n\choose k} k(n-k)T(k)T(n-k)
  $$
  
# Links
* [[Introduction To Graph Theory by Wilson|Wilson]]
* [[Trees]]