* (*Fraleigh 36.1*) Let $G$ be a [[Fundamental Constructs of Group Theory|group]] of order with [[Number Theory|prime]] power $p^n$ and let $X$ be a finite $G$-[[Group Action|set]]. Then
  $$
  |X| \equiv |X^g| \mod p
  $$
* Let $p$ be a prime. A group $G$ is a **$p$-group** if $\forall x \in G$, $\text{ord}(g)=p^k$ for some $k$. A [[Subgroup|subgroup]] is a **$p$-subgroup** if it is a subgroup of $G$ and also a $p$-group.

* (*Fraleigh 36.3*) **Cauchy's Theorem**. Let $p$ be a prime, and $G$ a finite group where $p$ divides $|G|$. Then $G$ has an element of order $p$ and a subgroup of order $p$.
	* *Proof*: Let $X$ be the set of all $p$-tuples such that 
	  $$
	  X= \set{(g_1,g_2,\dots, g_p)\mid  g_i \in G  \ \ g_1g_2\dots g g_p = e}
	  $$
	  Now $|X|$ is divisible by $p$ since for each tuple, $g_p=(g_1g_2 g_{p-1})^{-1}$.  Thus 
	  $$
	  |X| = |G|^{p-1}
	  $$
	  Consider the [[Permutations and Orbits|cycle]] $\sigma = (1,2,\dots, p)$ acting on $X$ so that 
	  $$
	  \sigma(g_1,\dots, g_{p-1},g_p) = (g_2,g_3,\dots,g_p,g_1)
	  $$
	  Note that $\sigma \in S_p$ (see [[Symmetric Group]]). The [[Cyclic Group|cyclic group]] $\braket{\sigma}\le S_p$ has order $p$. By (*Fraleigh 36.1*) 
	  $$
	  |X| \equiv |X^{\braket{\sigma}}| \mod p 
	  $$
	  The fixed points in $X^{\braket{\sigma}}$ correspond to tuples where $g_1=g_2=\dots=g_p$.  By the above congruence, there must be at least $p$ elements in $X^{\braket{\sigma}}$. Thus, there must be some element $a\in G$, $a\notin e$ such that 
	  $$
	  (a,a,\dots,a)\in X^{\braket{\sigma}} \implies a^p=e\implies \text{ord}(a) = p \implies |\braket{a}| = p
	  $$
	  
	  
* (*Fraleigh 36.4*) Let $G$ be a finite group. Then $G$ is a $p$-group if and only if $|G|$ is a power of $p$.
 

# Sylow Theorems
* We may view the Sylow Theorems as a counterpart to theorems about [[Abelian Group|finite abelian groups]]. 

* Let $H\le G$. The **normalizer** of $H$ in $G$, denoted $N[H]$ is defined as follows.
  $$
  N[H] = \set{g\in G \mid  gHg^{-1} = H}
  $$
  That is, it is the set of all elements in $G$ that leave $H$ invariant under conjugation. It is also the largest subgroup having $H$ as a [[Normal Group|normal subgroup]]


* (*Fraleigh 36.6*) Let $H$ be a $p$-subgroup of a finite group $G$. Then
  $$
  (N[H] : H) \equiv (G : H) \mod p
  $$
  See [[Cosets, Group Indices|group indices]].

* (*Fraleigh 36.7*) Let $H$ be a $p$-subgroup of a finite group $G$. If $p$ divides $(G:H)$, then $N[H]\ne H$. 

* (*Fraleigh 36.8*) **First Sylow Theorem**. Let $G$ be a finite group and let $|G|=p^nm$ where $n\ge 1$ and $p$ does not divide $n$. Then
	* $G$ contains a subgroup of order $p^i$ for each $1\le i\le n$.
	* Every subgroup $H\le G$ of order $p^i$ is a normal subgroup of a subgroup of order $p^{i+1}$. 
	* *Proof*: Argue by induction.  The base case follows from Cauchy's Theorem.
	  
	  In the general case, suppose we have a subgroup $H< G$ of order $p^i$ where $i<n$. . We have 
	  $$
	  (N[H]: H) \equiv (G:H) \equiv 0 \mod p
	  $$
	  Since $N[H]$ is the normalizer, $H\unlhd N[H]$. Therefore $N[H]/H$ is well defined and $p$ divides $|N[H]/H|$. We can apply Cauchy's theorem to the [[Factor Group|factor group]] to get a subgroup $K$ of order $p$.
	  
	  Let $\gamma : N[H] \to N[H]/H$ be the canonical [[Group Homomorphism|homomorphism]]. Then $H <\gamma^{-1}(K)\le N[H] < G$.  $H$ here has order $p^{i+1}$ and it is clearly normal in $\gamma^{-1}(K)$.   

* A **Sylow $p$-subgroup** $P$ of a group $G$ is a maximal $p$-subgroup of $G$. That is, it is not contained in any larger $p$-subgroup.
	* The Sylow $p$-subgroups of a group $G$ with order $|G|=p^nm$ is precisely the subgroups of order $p^n$. 
	* If $P$ is a Sylow $p$-subgroup, every conjugate $gPg^{-1}$ of $P$ is also a Sylow $p$-subgroup. 
* (*Fraleigh e36.12*) Let $G$ be a finite group and $p\ne q$ be primes that divide $|G|$. If $G$ has precisely one proper Sylow $p$-subgroup, it is a normal group so $G$ is not simple.
	* *Proof*: There is only one such subgroup $P$. Therefore every conjugate of $gPg^{-1}$ is a Sylow $p$-subgroup, and thus $gPg^{-1}=P$ for all $g\in G$. Thus, $P$ is normal. 

* (*Fraleigh 36.10*) **Second Sylow Theorem**. Let $P_1$ and $P_2$ be Sylow $p$-subgroups of a finite group $G$. Then $P_1$ and $P_2$ are conjugate subgroups of $G$.
	* *Proof*: Let $\mathcal{L}$ be the collection of left [[Cosets, Group Indices|cosets]] of $P_1$ and $P_2$ act on $\mathcal{L}$ by the group action
	  $$
	  y(xP_1) = (yx)P_1
	  $$
	  Where $y\in P_2$. Thus, $\mathcal{L}$ is a $P_2$-set. Therefore
	  $$
	  |\mathcal{L}_{P_2}| \equiv |\mathcal{L}| = (G:P_1) \not\equiv 0\mod p
	  $$
	  Therefore $|\mathcal{L}_{P_2}|\ne 0$. Let $xP_1\in \mathcal{L}_{P_2}$ then $\forall y\in P_2$
	  $$
	  yxP_1 = xP_1 \iff x^{-1}yxP_1 = P_1 \iff x^{-1}yx\in P_1
	  $$
	  Which implies
	  $$
	  x^{-1}P_2x \le P_1
	  $$
	  And since $|P_1|=|P_2|$ because they are both Sylow $p$-subgroups, we have 
	  $$
	  P_1=x^{-1} P_2 x
	  $$

* (*Fraleigh 36.11*) **Third Sylow Theorem**. If $G$ is a finite group and $|G|=p^nm$ where $p$ does not divide $m$, then the number of Sylow $p$-subgroups, denoted $n_p$ satisfies the following properties
	* $n_p$ divides $m$. In fact $m=(G : P)$ 
	* $n_p \equiv 1 \mod p$ 
	* $n_p = (G: N[P])$ where $P$ is any Sylow $p$-subgroup.
	* *Proof*: Let $\mathcal{P}$ be the set of all Sylow $p$-subgroups with $P\in\mathcal{P}$.  Let $P$ act on $\mathcal{P}$ by conjugation. We have $|\mathcal{P}|\equiv |\mathcal{P}^P| \mod p$. Note that $|\mathcal{P}|= n_p$.    
	  
	  If $T\in\mathcal{P}^P$ then $\forall x \in P, xTx^{-1}=T \implies P \le N[T]$.  Also $T\le N[T]$ and since both $P$ and $T$ are both Sylow $p$-subgroups of $G$, they are for $N[T]$ as well so the Second Sylow Theorem implies they are conjugates.  
	  
	  Since $T\unlhd N[T]$ it is only conjugate in $N[T]$ so $T=P$. Thus $N[P]$ is a stabilizer of $\mathcal{P}^P$  and $n_p= (G: N[P])$ which proves the third statement. Also 
	  $$
	  n_p =|\mathcal{P}|\equiv |\mathcal{P^P}|\equiv 1 \mod p
	  $$
	  which proves the second statement. 
	  
	  Also let $G$ act on $\mathcal{P}$ by conjugation. There is only one orbit in $\mathcal{P}$ under G by the Second Sylow Theorem since they are conjugates of each other. We therefore have for $P\in\mathcal{P}$
	  $$
	  |\mathcal{P}| = |\text{Orb}(P) | =(G:G^P) \equiv 0 \mod |G|
	  $$
	  By the Orbit Stabilizer Theorem, it follows that $n_p=(G : G^P)=(G: N[P])$ which divides $|G / N[P]| = (G : P)$ which proves the first statement. 

* (*Fraleigh e36.16*) Let $G$ be a finite group and $p$ be a prime dividing $|G|$. Let $P$ be a Sylow $p$-subgroup.  Then 
  $$
  N[N[P]] = N[P]
  $$
	* *Idea*: From the Third Sylow Theorem, $N[P]$ is a stabilizer of the group action on $\mathcal{P}$ by $P$. 



* (*Fraleigh 37.1*) Every finite $p$-group is solvable. 
	* *Idea*: From the First Sylow Theorem, each $p$-subgroup $H_i$ is normal in $H_{i+1}$.  All $H_{i+1} / H_i$ have order $p$. By (*Fraleigh 10.11*) they are all [[Cyclic Group|cyclic]] and hence Abelian. 

* (*Fraleigh 37.4*) The center of a finite nontrivial $p$-group is nontrivial.
	* *Proof*: In the Classic [[Group Action|class equation]], $p$ divides $|Z(G)|$. Since $e\in Z(G)$, there must exist $a\in Z(G)$ $a\ne e$
* (*Fraleigh e36.21*) Let $p$ be a prime. A finite group $G$ of order $p^n$ contains a normal [[Subgroup Series|series]]. where $|H_i|=p^i$ for $0\le i\le n$. 
	* *Idea*:The normal series in question is the ascending central series of $G$
* (*Fraleigh 37.5*) Let $H,K\unlhd G$ such that $H\cap K = \set{e}$ and $H\vee K = G$. Then 
  $$
  G\cong H\times K
  $$
  See [[Direct Product of Groups|direct products]]
	* *Idea*: Show that $hk=kh$ for $k\in K$ and $h\in H$ using the [[Commutator Group|commutator]]. Then construct a homomorphism $\phi:H\times K \to G$ defined by  $\phi(h,k)=hk$. What remains is to show that $\phi$ is an [[Group Isomorphism|isomorphism]]. 

* (*Fraleigh 37.6*) For a prime number $p$, every group $G$ of order $p^2$ is [[Abelian Group|abelian]].
	* *Proof*: If $G$ is not cyclic, there must exist $a,b\in G$ such that $\text{ord}(a) =\text{ord}(b) =p$ and $b\notin \braket{a}$. 
	  
	  Clearly $\braket{a}, \braket{b} \unlhd G$ by the First Sylow Theorem.  
	  
	  Also $\braket{a}\cap \braket{b} = \set{e}$. Also $\braket{a}\vee \braket{b} = G$ since $|G| = p^2$. 
	  
	  Therefore (*Fraleigh 37.5*) can be applied to get $G\cong \braket{a}\times \braket{b}$ which proves that it is Abelian by the [[Abelian Group|Fundamental Theorem of Finitely Generated Abelian Groups]]. 

* (*Fraleigh 37.7*) If $p$ and $q$ are distinct primes with $p<q$, then every group $G$ of order $pq$ has a single subgroup of order $q$ which is normal in $G$. Hence $G$ is not simple.
  
  If $q\not\equiv 1 \mod p$ then $G$ is Abelian and Cyclic. 

* (*Fraleigh 37.9*) No group of order $p^r$ for $r>1$ is simple where $p$ is prime. 


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]