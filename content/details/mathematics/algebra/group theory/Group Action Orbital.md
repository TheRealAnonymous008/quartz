* Let $G$ be a [[Transitive Group|transitive]] [[Permutations and Orbits|permutation]] group [[Group Action|acting]] on $X$. Of interest to us is $G$ acting on the pairs $X^2$.  The orbits of $G$ acting on $X^2$ are sometimes called  **orbitals** [^orbitals]

* The **diagonal orbital** is defined as the set 
  $$
  \set{(x,x) \mid x\in X}
  $$
* If $\Omega\subseteq X^2$, then the **transpose** is defined as
  $$
  \Omega^T = \set{(y,x)\mid (x,y)\in \Omega}
  $$
	* $\Omega^T$ is $G$-invariant if and only if $\Omega$ is. 
* If $\Omega$ is an orbit of $G$,, then there are only two cases
	* $\Omega = \Omega ^T$, the **symmetric case**
	* $\Omega\cap \Omega^T=\emptyset$ , the disjoint case. 

* (*Godsil 2.4.1*) Let $G$ be a group acting transitively on $X$, where $x\in X$. Then there is a one-to-one correspondence $f$
  $$
  f: X^2/ G \mapsto X/G_x
  $$

* If $\Omega$ is symmetric, then the corresponding orbit of $G_x$ is said to be **self-paired**.  [^self-pairing]

[^orbitals]: Note the similarities with [[Matrix|Matrices]]
[^self-pairing]: One nice example of this. If we consider a group acting on a graph with vertex set $X$ and arc-set $\Omega$ then if $\Omega$ is self-paired, the graph is undirected. Otherwise it is [[Directed Graph|oriented]]. 

* (*Godsil 2.4.2*) Let $G$ be a transitive permutation group on $X$ and $\Omega\in X^2/G$. Suppose $(x,y)\in \Omega$. Then $\Omega$ is symmetric if and only if there is a permutation $g\in G$ such that 
  $$
  gx = y \wedge gy =x
  $$
* A permutation group $G$ on $X$ is **generously transitive** if, for any distinct $x,y\in X$ there is a permutation that swaps them. 
	* All $\Omega \in X^2/G$ are symmetric if and only if $G$ is generously transitive. 

* (*Godsil e2.11*) Let $G$ be a transitive permutation group on $X$. $G$ has a symmetric nondiagonal orbit on $X^2$ if and only if $|G|$ is even. 
	* *Proof*: If $G$ has a symmetric nondiagonal orbit $\mathcal{O}$ on $X^2$  where $(x,y)\in \mathcal{O}$ then by its symmetry, $(y,x)\in \mathcal{O}$. We can, therefore, partition  $\mathcal{O}$ into two groups. Hence $|\mathcal{O}|$ is even and by the Orbit-Stabilizer theorem, $|G|$ is even. 
	  
	  Conversely, if $|G|$ is even, then by [[p-Group and the Sylow Theorems|Cauchy's theorem]], $G$ contains $\tau$ which is of order $2$. By transitivity, it must swap at least two elements $x,y$. The orbit $\text{Orb}_G((x,y))$ contains both $(x,y)$ and $(y,x)$. Clearly $x\ne y$ and also $\mathcal{O}$ is closed under swapping, so it is symmetric nondiagonal.
#  Links
* [[Algebraic Graph Theory by Godsil and Royle]]