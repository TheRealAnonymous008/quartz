* Let $E$ be a non-empty finite set and $\mathcal{F}=\{S_1,\dots, S_m\}$ a family of not necessarily distinct, non-empty subsets of $E$. A **transversal** of $\mathcal{F}$ is a set of $m$ distinct element of $E$, one chosen from each set $S_i$.

* Given a family $\mathcal{F}$ of subsets of $E$, an **independent transversal** is a transversal that is also an independent set of a matroid $M$.

* A **partial transversal** of a family of sets $\mathcal{F}$ is a transversal of some subfamily of $\mathcal{F}$
	* (*Wilson 26.2*) $\mathcal{F}$ has a partial transversal of size $t$ if and only if the union of any $k$ of the subsets in $\mathcal F$ contains at least $k+t-m$ elements
	* (*Wilson 26.3*) $X$ contains a partial transversal of $\mathcal F$ of size $t$ if and only if, for each subset $A$ of $\{1,\dots,m\}$ then
	  $$
	  \left|\left(\bigcup_{j\in A} S_j\right)\cap X\right| \ge |A|+t-m
	  $$
	  That is, removing some elements for all members of the family does not change the Hall condition.

* Let $E$ be a non-empty finite set and $\mathcal{F}=\{S_1,\dots, S_m\}$ and $\mathcal{G}=\{T_1,\dots, T_m\}$ be families of non-empty subsets of $E$, then a **common transversal** is a transversal for both $\mathcal{F}$ and $\mathcal{G}$.
	* (*Wilson 27.3*) A common transversal exists if and only if for all subsets $A$ and $B$ of $\{1,\dots, m\}$. 
	  $$
	  \left|
	  \left(\bigcup_{i\in A}S_i\right)
	  \cap
	  \left(\bigcup_{j\in B}T_j\right)
	  \right|\ge |A|+|B|-m
	  $$


# Other Theorems 
* (*Wilson e26.8*) Let  $T_1, T_2$ be transversals of $\mathcal{F}$. $x\in T_1$. Then, there exists an element $y\in T_2$ such that $$(T_1-\{x\})\cup \{y\}$$ is also a transversal. 
	* *Proof*: Assume $T_1$ and $T_2$ are distinct transversals. Note that, because they are of the same size, then there exists $x,y$ such that 
	  $$
	  \begin{equation} \begin{split}
	  x \in T_1 &\ \ \ x \notin T_2 \\
	  y \notin T_1 &\ \ \ y \in T_2
	  \end{split}\end{equation}
	  $$
	  
	  We show that $x,y\in S_i$, for some $S_i\in \mathcal{F}$. Suppose by contradiction. As above we may have
	  $$
	  \begin{equation} \begin{split}
	  x \in S_x &\ \ \ x \notin S_y \\
	  y \notin S_x &\ \ \ y \in S_y
	  \end{split}\end{equation}
	  $$
	  Now, since $T_1$ is a transversal, it must include an element $y'\in S_y$. Such an element is not included in $T_2$ since it already includes $y$. We argue similarly for $T_2$ and $x$. In summary, 
	  $$
	  \begin{equation} \begin{split}
	  \exists y'\in S_y &: y'\in T_1, y'\notin T_2 \\
	  \exists x'\in S_x &: x'\notin T_1, x'\in T_2 
	  \end{split}\end{equation}
	  $$
	  
	  But now, observe we are back to the same problem as before. This is effectively an argument by infinite descent, leading to the desired contradiction.
	  
	  With this, we have that $x,y\in S_i$.  It follows that , since both $T_1$ and $T_2$ are transversals, $y$ may be properly matched to the $i$-th element and no other element. Replacing $x$ with $y$ in $T_1$ indeed gives another transversal.

  * (*Wilson e26.10*) A family $\mathcal{F}$ of subsets of $E$ has a transversal containing a given subset $A$ if and only if 
	  * $\mathcal{F}$ has a transversal 
	  * $A$ is a partial transversal of $\mathcal{F}$.
	  * (*Proof*) Observe that in the lens of a transversal matroid $A$ is an independent set of the transversal matroid $M$ determined by $\mathcal{F}$.
	    
	    Thus, by the basis definition of a matroid, $A$ can be extended to a basis of $M$
	    
	    Since $\mathcal{F}$ has a transversal, every basis of $M$ must be a transversal, and this basis contains $A$ as desired. 

* (*Wilson 33.1*) **Rado's Theorem** - Let $M$ be a [[Matroid Theory|matroid]] on a set $E$, and let $\mathcal{F}=\{S_1,\dots, S_m\}$ be a  family of non-empty subsets of $E$. Then $\mathcal{F}$ has an independent transversal if and only if the union of any $k$ of the subsets $S_i$ contains an independent set of size at least $k$.
	* Applying it to the [[Matroid Types|discrete matroid]] on $E$ gives [[The Matching Problem and Flow Networks|Hall's Theorem]].

* (*Wilson 33.2*) A family $\mathcal{F}$ has an independent partial transversal of size $t$ if and only if the union of any $k$ of the subsets $S_k$ contains an independent set of size at least $k+t-m$