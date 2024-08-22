* The [[Fundamental Constructs of Ring Theory|ring]] $RG$ defined as follows is called the **[[Fundamental Constructs of Group Theory|group]] ring** of $G$ over $R$.
	* $RG$ consists of the set of all formal sums $\sum_{i=I}a_i g_i$, where $a_i\in R$ and $g_i\in G$ where all but a finite number of $a_i$ are $0$
	* The sum of two elements of $RG$ is defined as 
	  $$
	  \left(\sum_{i\in I} a_ig_i\right) + \left(\sum_{i\in I} b_ig_ii\right) = \sum_{i\in I} (a_i+b_i)g_i
	  $$
	* The product of two multiplications is defined using multiplications for both $R$ and $G$ as follows 
	  $$
	  \left(\sum_{i\in I} a_ig_i\right) \left(\sum_{i\in I} b_ig_i\right) = \sum_{i\in I}\left(\sum_{g_jg_k=g_i} a_jb_k\right)g_i 
	  $$
	  Intuitively, we distribute the sums to get $a_jg_jb_kg_k$ and replace that with $a_jb_kg_i$.
* If $F$ is a field, we call  $FG$ as the **group algebra** of $G$ over $F$.


* (*Fraleigh 24.4*) If $G$ is any group written multiplicatively and $R$ is a [[Commutative Ring]] with nonzero [[Division Ring and Rings with Unity|unity]] then $(RG,+,\cdot)$ is a ring.

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]