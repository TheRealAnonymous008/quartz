* A **subnormal (subinvariant) series** of a group $G$ is a finite sequence $H_0,H_1,\dots, H_n$ of [[Subgroup|subgroups]] of $G$ such that $H_i < H_{i+1}$ and $H_i$ is a [[Normal Group|normal subgroup]] of $H_{i+1}$ and $H_0=\set{e}$ and $H_n=G$.
* A **normal (invariant) series** of $G$ is a finite sequence $H_0,H_1,\dots, H_n$ of normal subgroups of $G$ such that $H_i < H_{i+1}$, $H_0=\set{e}$ and $H_n=G$.

* A subnormal (normal) series $\set{K_j}$ is a **refinement** of a subnormal (normal) series $\set{H_i}$ of a group $G$ if $\set{H_i}\subseteq \set{K_j}$. That is, if each $H_i$ is one of the $K_j$.

* Two subnormal (normal) series $\set{H_i}$ and $\set{K_j}$ of the same group $G$ are **isomorphic** if there is a one-to-one correspondence between the collections of factor groups $\set{H_{i+1}/H_i}$ and $\set{K_{j+1}/K_j}$ such that the corresponding [[Factor Group|factor groups]] are isomorphic. 

* (*Fraleigh 35.11*) **Schreier Theorem** Two subnormal (normal) series of a group $G$ have isomorphic refinements. 
	* *Proof*: Consider two subnormal series $\set{H_i}$ and  $\set{K_j}$ with $n$ and $m$ elements respectively. 
	  
	  $\forall i : 0\le i < n$, form the chain 
	  $$
	  H_i = H_i(H_{i+1}\cap K_0) \le H_i (H_{i+1} \cap K_1)\le\dots\le H_i(H_{i+1} \cap K_m) = H_{i+1}
	  $$
	  That is, we insert $m-1$ groups between each $H_i$ and $H_{i+1}$. Denote $H_{i,j}=H_i(H_{i+1} \cap K_j)$ such that we have a new chain of groups of $nm+1$ not necessarily distinct groups and where $H_{i,0}=H_i$:
	  $$
	  \begin{split}
	  \set{e}& =H_{0,0} &\le H_{0,1} & \le \dots & \le H_{0,m-1} & \le H_{1,0}  \\
	  & & \le H_{1,1} & \le \dots & \le  H_{1,{m-1}} & \le H_{2,0} \\
	  & & \le \dots & \\ 
	  & & \le H_{n-1,1} & \le \dots & \le  H_{n-1,{m-1}} & \le H_{n-1,m} \\
	  & & = G
	  \end{split}
	  $$
	  Construct a similar series for $K$, setting $K_{j,i}=K_j(K_{j+1}\cap H_i)$ for $0\le j\le m-1$ .
	  
	  The  Zassenhaus Lemma gives us 
	  $$
	  H_{i,j+1} / H_{i,j} \cong K_{j,j+1} / K_{j,i}
	  $$
	  Which proves the theorem for subnormal series. For normal series, we note how each $H_{i,j}$ and $K_{j,i}$ are also normal in $G$ by (*Fraleigh 34.4*) 

* A subnormal series $\set{H_i}$ of a group $G$ is a **composition series** if all the factor groups $H_{i+1}/H_i$ are simple.
  
  A normal series $\set{H_i}$ of $G$ is a **principal series** if all the factor groups $H_{i+1}/H_i$ are simple.

* (*Fraleigh 35.15*) **Jordan-Holder Theorem** Any two composition (principal) series on $G$ are isomorphic.
	* *A composition series is a factorization of a group into simple factor groups*. Such a factorization is unique.
	* $H_{i+1}$ is simple if and only if $H_i$ is a maximal normal subgroup. For a composition series, each $H_i$ must a be a maximal normal subgroup of $H_{i+1}$.
	* For a principal series, each $H_i$ must be a maximal normal subgroup of $H_{i+1}$ that is also normal on $G$.
* (*Fraleigh 35.16*) If $G$ has a composition (principal) series, and if $N$ is a proper normal subgroup of $G$, then there exists a composition (principal) series containing $N$. 


* A group $G$ is **solvable** if it has a composition series $\set{H_i}$ such that all factor groups $H_{i+1}/H_i$ are [[Abelian Group|abelian]]. 
	* For a solvable group, every composition series $\set{H_i}$ must have abelian factor groups $H_{i+1}/H$.

* Let $G$ be a group and $Z(G)$ be its [[Abelian Group|center]].  Also, let $Z_i$ be the center of $G/Z_{i-1}(G)$, where $Z_0(G)= Z(G)$. 
  
  The series
  $$
  \set{e} \le Z(G) \le Z_1(G) \le \dots 
  $$
  is called the **ascending central series of $G$**.

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]