* An **Abelian Group** is a group that is **commutative**. That is $\forall x, y\in G$ 
  $$
  x\ast y=y\ast x
  $$
* For a subgroup $H$ of an Abelian group $G$, the partition of $G$ into left [[Cosets, Group Indices|cosets]] of $H$ and the partition of right cosets are the same. 

* (*Fraleigh 38.12*) Every finitely generated Abelian group is isomorphic to a group of the form
  $$
  \mathbb{Z}_{m_1}\times \dots \times \mathbb{Z}_{m_r} \times \mathbb{Z}\times \dots \times \mathbb{Z}
  $$
  Where $m_i$ divides $m_{i+1}$ for $i=1,\dots, r-1$.
	* *Proof*:  Let $F=\mathbb{Z}^n$. Consider the homomorphism $\phi:F\to G$ from (*Fraleigh 38.8*) see [[Free Abelian Group|here]]. Let $K=\text{Ker}(\phi)$.
	  Apply (*Fraleigh 38.11*) to get a basis for $F$ with a basis of the form $\set{x_1,\dots, x_k}$ and $\set{m_1x_1,\dots,m_sx_s}$ is a basis for $K$ and $m_i$ divides $d_{m+1}$. 
	  
	  Now $G\cong F/K$ by the Fundamental [[Group Homomorphism|homomorphism]] theorem. But also
	  $$
	  \begin{split}
	  F/K &\cong (\mathbb{Z}^n ) / (m_1 \mathbb{Z}\times \dots\times m_s\mathbb{Z} \times \set{0} \times \dots \times \set{0}) \\ 
	  &\cong \mathbb{Z}_{m_1} \times \dots \times \mathbb{Z}_{m_s} \times \dots \times \mathbb{Z} \times \dots \times \mathbb{Z}
	  \end{split}
	  $$


* **Fundamental Theorem of Finitely Generated Abelian Groups**: Every finitely generated Abelian group $G$ is [[Group Isomorphism|isomorphic]] to the [[Direct Product of Groups|direct product]] of the form 
  $$
  \mathbb{Z}_{(p_1)^{r_1}} \times \dots \times \mathbb{Z}_{(p_k)^{r_k}} \times \mathbb{Z}\times \dots\times \mathbb{Z}
  $$
  Where $p_i$ are primes, not necessarily distinct, and $r_i\in \mathbb{Z}^+$. 
  
  The direct product is unique except for rearrangement of the factors. The number of factors of $\mathbb{Z}$ is the unique **Betti Number** of $G$. 
	* Apply (*Fraleigh 38.12*). Note that for each $\mathbb{Z}_{m_i}$ there exists a prime power decomposition by the [[Number Theory|fundamental theorem of arithmetic]].
	  
	  Let $T$ be the torsion subgroup of $G$. The Betti number is the rank of $G/T$ which is invariant and thus unique.
	* Let $T_p\le T$ be the subgroup obtained by elements of the torsion subgroup of $G$ with prime order $p$. It can be shown that any prime power decomposition of $T$ has each subgroup $T_p$ isomorphic to the direct product of those cyclic factors of order some power of $p$.  Thus, the decomposition into products of cyclic groups is unique.
		* This holds because there exists a basis $Y=\set{d_1y_1,\dots,d_ny_n}$ such that  each $d_i$ divides $d_{i+1}$. We also have that $d_1=p$ by the definition of $T_p$. 
	* Additionally, let $G[n]=\set{x\in G \mid nx = 0}$. It can be shown to be a subgroup of $G$.  
	  
	  Note that $Z_{p^r}[p] \cong Z_p$ for any $r\ge 1$ and prime $p$. because 
	  $$
	  \mathbb{Z}_{p^r} [p] \cong \braket{p^{r-1}} \cong \mathbb{Z}_p 
	  $$ 
	  Thus if each $r_i\ge 1$. 
	  $$
	  (\mathbb{Z}_{p^{r_1}} \times \dots \times \mathbb{Z}_{p^{r_2}})[p] \cong \mathbb{Z}_p^m 
	  $$
	* To show the uniqueness of the prime power decomposition we have that: 
	  $$
	  T_p \cong \mathbb{Z}_{p^{r_1}}\times \dots \times \mathbb{Z}_{p^{r_n}} \cong \mathbb{Z}_{p^{s_1}} \times \dots \times \mathbb{Z}_{p^{s_m}} \cong \mathbb{Z}_{p}^m \cong \mathbb{Z}_p^n 
	  $$
	  Where $\set{r_i}$ and $\set{s_i}$ are sorted in ascending order. Thus $m=n$. 
	  
	  Finally, argue by induction that each $r_i=s_i$.  Consider  $p^{r_j}T_p$.  For each $i$, we have
	  $$
	  p^{r_i} \mathbb{Z}^{p^{r_i}} \cong \set{0} \cong p^{r_i}\mathbb{Z}^{p^{s_i}} \cong \mathbb{Z}^{r_i}
	  $$
	  That is, $r_i\ne s_i$ gives us two decompositions, one of which has an extra factor over the other. Hence a contradiction 
	* Finally, to show the decomposition for the whole torsion group $T$, we note that we can decompose $T$ into a direct product of all $T_p$ where $p$ is a prime factor of $|T|$. Each $T_p$ has a unique decomposition therefore so does $T$. 

* (*Fraleigh 11.15*) The finite indecomposable Abelian groups are exactly the cyclic groups of [[Number Theory|prime]] power order.
* (*Fraleigh 11.16*) If $G$ is a finite Abelian group, and if $m$ divides $|G|$, then $G$ has a subgroup of order $m$.
* (*Fraleigh 11.17*) If $m$ is a not divisible by the square of a prime number, then every Abelian group of order $m$ is cyclic.

* The **torsion subgroup** of Abelian group $G$ is the elements of finite order in $G$. It is denoted $A_T$ 
  
  An Abelian group is **torsion free** if $e$ is the only element of finite order 
  
  (*Fraleigh e11.43*) Every Abelian group is the direct product of its torsion subgroup and of a torsion-free subgroup. 


* Every Abelian Group is [[Normal Group|Normal]].

* The **center** of a group $Z(G)$ is the Abelian subgroup of $G$ defined as 
  $$
  Z(G)=\{z\in G\mid zg=gz \space \space \forall g\in G\}
  $$
* Another important normal subgroup is the [[Commutator Group]]. 

# Topics
* [[p-Group and the Sylow Theorems]] - certain results about $p$-groups involve Abelian groups.
* [[Free Abelian Group]]


# Links 
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]