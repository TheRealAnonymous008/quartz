* A **subnormal (subinvariant) series** of a group $G$ is a finite sequence $H_0,H_1,\dots, H_n$ of [[Subgroup|subgroups]] of $G$ such that $H_i < H_{i+1}$ and $H_i$ is a [[Normal Group|normal subgroup]] of $H_{i+1}$ and $H_0=\set{e}$ and $H_n=G$.
* A **normal (invariant) series** of $G$ is a finite sequence $H_0,H_1,\dots, H_n$ of normal subgroups of $G$ such that $H_i < H_{i+1}$, $H_0=\set{e}$ and $H_n=G$.

* (*Fraleigh e35.23*) If 
  $$
  H_0 = \set{e} < H_1 <H_2<\dots < H_n = G
  $$
  is a subnormal (normal ) series then 
  $$
  \text{ord} (G) = \prod_{i} \text{ord} (H_{i+1} / H_i)
  $$
 

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
* (*Fraleigh e35.27*) Let $\set{H_i}$ be a composition series for group $G$. Let $N\unlhd G$ be a simple group.  The distinct groups among $H_0, H_0N,\dots, H_n N$ also form a composition series for $G$.
	* *Proof*: By the Isomorphism Theorems we have the following
	  $$
	  \begin{split}
	  (H_iN)/ (H_{i-1}N) &\cong H_i/[H_i\cap (H_{i-1}N)] \\
	  &\cong \frac{H_i}{H_{i-1}} \bigg/ \frac{H_i\cap (H_{i-1} N)}{H_{i-1}}
	  \end{split} 
	  $$
	  Note that $H_i/H_{i-1}$ is simple. Therefore ${[H_i\cap (H_{i-1} N)} ]/ {H_{i-1}}$ is isomorphic to either $\set{e}$ or $H_i/H_{i-1}\cong (H_i N)/(H_{i-1}N)$. 
	  
	  In either case, $(H_iN)/(H_{i-1}N)$ is simple which proves the theorem.
* (*Fraleigh e35.28*) Let $\set{H_i}$ be a composition series for $G$. Let $N\unlhd G$ and $\gamma : G\to G/N$ be the canonical [[Group Homomorphism|homomorphism]]. The distinct groups among $\gamma[H_i]$ form a composition series for $G/N$.
	* *Proof*: Observe that the map $\psi: H_i N \to \gamma(H_i)/\gamma[H_{i-1}]$  defined by
	  $$
	  \psi(h,n ) = \gamma (h_in) \gamma[H_{i-1}]
	  $$
	  Is a homomorphism such that 
	  $$
	  \text{Ker} (\psi) = H_{i-1} N 
	  $$
	  Therefore by the First Isomorphism Theorem
	  $$
	  \gamma(H_i) / \gamma [H_{i-1}] \cong (H_iN) / (H_{i-1}N) 
	  $$
	  And the proof from (*Fraleigh e35.27*) shows that the above quotient is simple. Therefore, the distinct groups among $\gamma[H_i]$ form a composition series.


* (*Fraleigh e35.24*) An infinite Abelian group has no composition series.
	* *Idea*: Let $G$ be the infinite Abelian group. Clearly $\set{e}<G$ is not a composition series as $G$ has a proper normal subgroup. By (*Fraleigh e35.23*), however, it is impossible to create a composition series using finite groups since the product of their orders is finite while $\text{ord}(G)=\infty$ 

* A group $G$ is **solvable** if it has a composition series $\set{H_i}$ such that all factor groups $H_{i+1}/H_i$ are [[Abelian Group|abelian]]. 
	* For a solvable group, every composition series $\set{H_i}$ must have abelian factor groups $H_{i+1}/H$.
	* (*Fraleigh e35.25*) A finite [[Direct Product of Groups|direct product]] of solvable groups is solvable. 
	* (*Fraleigh e35.26*) Let $K\le G$. If $G$ is solvable then $K$ is solvable. 
		* *Proof*: Consider a composition series $\set{H_i}$ for $G$. The set $\set{K\cap H_i}$ forms a composition series for $K$ as shown below. Note that $H_{i-1}(K\cap H_i)$ because $H_{i-1}$ is Abelian and so is $(K\cap H_i)$ so $H_{i-1}(K\cap H)$ is Abelian. The Second and Third [[Group Isomorphism|Isomorphism]]Theorems can be applied
		  $$
		  \begin{split}
		  (K\cap H_i) / (K\cap H_{i-1}) & \cong [H_{i-1} (K\cap H_i)] / [H_{i-1}]  \\ &\cong [(K\cap H_i)]H_{i-1}  / [H_{i-1}] \\
		  &\cong (K\cap H_i)\\
		  \end{split} 
		  $$
		  Which proves the theorem since $(K\cap H_i)$ is Abelian.
	* (*Fraleigh e35.29*) A homomorphic image of a solvable group is solvable. 
		* *Proof*: Use the same argument as (*Fraleigh e35.27*) and (*Fraleigh e35.28*) using the canonical map $\gamma$ and solvable composition series $\set{H_i}$. 
		  
		  Note that $(H_iN)/(H_{i-1}N)$ is Abelian. Therefore, the homomorphic image is solvable.


* Let $G$ be a group and $Z(G)$ be its [[Abelian Group|center]].  Also, let $Z_i$ be the center of $G/Z_{i-1}(G)$, where $Z_0(G)= Z(G)$. 
  
  The series
  $$
  \set{e} \le Z(G) \le Z_1(G) \le \dots 
  $$
  is called the **ascending central series of $G$**.

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]