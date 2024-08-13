* Let $H\le G$. 
  
  The **left coset** of $H$ containing $a$ is defined as 
  $$
  aH=\{ah \mid h\in H\}
  $$
  and the **right coset** of $H$ containing $a$ is defined as 
  $$
  Ha=\{ha\mid h\in H\}
  $$
  
* (*Fraleigh 10.1*) The cosets partition a group into [[Relation|equivalence classes]].
	* More specifically the left coset expresses the equivalence relation 
	  $$
	  a\sim b\iff a^{-1}b\in H
	  $$
	  
	* The right coset expresses 
	  $$
	  a\sim b\iff ab^{-1}\in H
	  $$
	  
* (*Fraleigh e10.34*) There are the same number of left and right cosets of a subgroup $H\le G$. That is, we can establish a one-to-one map between left and right cosets.  
	* *Intuition*: Note that $h^{-1}\in H$ and that the inverse $a^{-1}\in G$ is unique. Map $ah\in aH$ to $h^{-1}a^{-1}\in Ha^{-1}$
* Every coset of a subgroup $H\le G$ has the same number of elements as $H$.
* Let $H,K\le G$. 
  
  The **double coset** is the set defined as 
  $$
  HxK=\{hxh\mid h\in H, k\in K\}
  $$
  
	* This forms an equivalence class where $x\sim y$ if and only if there exists $h\in H$ and $k\in K$ such that $hxk=y$.
# Group Index
* Let $H\le G$, the number of left cosets of $H$ in $G$ is called the **index** of $H$ and $G$. This is denoted $(G:H)$. 
* (*Fraleigh 10.14*) Let $H,K\le G$ such that $K\le H\le G$ and suppose $(H:K)$ and $(G:H)$ are both finite. Then $(G:K)$ is finite and 
  $$
  (G:K)=(G:H)(H:K)
  $$
# Links
* [[Subgroup]]
* [[Normal Group]]
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]