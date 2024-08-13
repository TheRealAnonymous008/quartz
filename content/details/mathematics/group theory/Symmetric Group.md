* The **Symmetric Group** of order $n$ is the group whose set is the set of all [[Permutations and Orbits|permutations]] of $n$ elements and whose binary operation is the composition of permutations. It is denoted as $S_n$.
* A **Permutation Group** is a group whose set consists of permutations and whose binary operation involves composing two permutations. It is a [[Subgroup]] of $S_G$. 

* (*Fraleigh 8.16*) **Cayley's Theorem**: Every group is [[Group Isomorphism|isomorphic]] to a permutation group.
	* *Intuition*: Every element of the group induces a group action on the group which permutes the group elements. A mapping from group elements to permutations of the group elements gives us an isomorphism to a permutation group.
	* We can define two maps. Let  $\lambda_x : G\to G$ be the permutation on the group defined as $\lambda_x(g) = xg$  $\forall g\in G$
	  
	  The map $\phi : G\to S_G$ defined by $\phi(x) = \lambda_x$ is the **left regular representation** of $G$. 
	  
	  Similarly, let $\rho_x:G\to G$ be the permutation on the group defined as $\rho_x(g) = gx$ $\forall g\in G$.
	  
	  The map $\mu: G\to S_G$ defined by $\mu(x) = \rho_{x^{-1}}$ is the **right regular representation** of $G$.
	* We can think of the left and right regular representations as encoding [[Group Action|group actions]] and defining a bijection from a group element to its corresponding group action.

* Let $A$ be a set. Then $H\le S_A$ is **transitive on** $A$ if $\forall a,b\in A$ $\exists \sigma$ such that $\sigma(a) =b$.  

* (*Fraleigh e9.29*) Every subgroup $H\le S_n$ for $n\ge 2$, either all permutations in $H$ are even or exactly half of them are even.
	* *Intuition*: Any odd permutation $\tau$ has a corresponding group action which maps the group to itself. In $\tau H$, the evens become odds and the odds become evens but the number of elements must stay the same because the group elements did not change.
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]] 