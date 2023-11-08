* Let $M$ be a matroid defined on set $E$. Let $A\subseteq E$.
* Two matroids $M_1$ and $M_2$ are said to be **isomorphic** if there is a bijection between their underlying sets $E_1$ and $E_2$ that preserves independence. 

# Operations on Matroids
* The **Matroid contraction** of $M$ to $A$ is denoted as $M . A$ is a matroid whose cycles are the minimal members of the collection $\{C_i \cap A\}$ where $C_i$ is a cycle of $M$. 
* The **Matroid restriction** of $M$ to $A$ is denoted as $M\times A$ is a matroid whose cycles are those contained in $A$.
* A **Minor** is a matroid obtained either by restriction or construction
	* (*Wilson e31.9.1*) For $A\subseteq B\subseteq E$, then 
	  $$
	  M.B.A=M.A
	  $$

		* Let $C$ be a cycle of $M$ Performing $M.B.A$ gives a matroid with the minimal members of $\{C \cap B \cap A\}$ as a cycle. 
		  
		  Since $A\subseteq B$, $A\cap B = A$. Therefore, the above is equivalent to $\{C\cap A\}$ and the corresponding matroid is $M.A$.

	* (*Wilson e31.9.2*) For $A\subseteq B\subseteq E$, then 
	  $$
	  M\times B\times A=M\times A
	  $$
		* *Proof*: Performing $M\times B\times A$ gives us a new matroid whose cycles are contained in $B\cap A$. 
		  
		  Since $A\subseteq B$, any cycle contained in $B\cap A=A$ 
		  
		  So we could get the same result if we performed $M\times A$ instead.

* Let $M_1, \dots, M_k$ be matroids on the same set $E$. Then, a new matroid called their **union**, denoted $$M_1\cup\dots\cup M_k$$can be defined by taking as independent set, all possible unions of an independent set in $M_1, M_2, \dots, M_k$.
	* (*Wilson 33.3*) Let $r_1,\dots, r_k$ be rank functions to their corresponding matroids. Then, the rank function $r$ of the union is given by 
	  $$
	  r(X)=\min_{A\subseteq X}\left(r_1(A) + \dots +r_k(A) + |X-A|\right)
	  $$

# Theorems 
* (*Wilson e31.10.1*) Any minor of a graphic matroid is also graphic. 
	* *Proof*: Since matroid contraction and matroid restriction correspond to [[Operations on Graphs|edge contraction]] and edge deletion we have that the resulting matroid minor is still graphic as it corresponds to a new graph with some edges removed or contracted, and no new edges were added so no new [[Spanning Trees and Forests|spanning forests]] were added. 
* (*Wilson e31.10.2*) Any minor of a cographic matroid is also cographic. 
	* *Proof*: Similar to (*Wilson e31.10.1*), except applying to [[Trees|cotrees]].  
* (*Wilson e31.10.3*) Any minor of a regular matroid is also regular.
	* *Proof*: If $M$ is regular, then it is representable in every field $F$. So, there exists a map $\phi$ and a vector space $V$ that maps independent sets of $M$ to linearly independent subsets of $V$. 
	  
	  Performing either matroid restriction or matroid contraction is equivalent to considering a subset of a set linearly independent vectors. This subset is also linearly independent so the resulting matroid is also regular 
* (*Wilson e31.10.4*) Any minor of a binary matroid is also binary. 
	* *Proof*: Similar to (*Wilson e31.10.3*) except restricted to the field of $\mathbb{Z}_2$. 

# Links 
* [[Matroid Definitions and Constructs]]
* [[Matroid Types]]