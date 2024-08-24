* If every nonzero element of $R$ is a unit, then $R$ is a **division [[Fundamental Constructs of Ring Theory|ring]]**. 
	* If it is [[Commutative Ring|commutative]], we call it a [[Field]].
	* Otherwise we call it a **strictly skew field**.

* Implicitly, a division ring is a [[Ring with Unity]]

* (*Fraleigh e19.23*) A division ring contains exactly two idempotent elements

* A corollary of (*Fraleigh 19.15*) is that for $n\in \mathbb{Z}^+$ and division ring $R$ such that $\text{char}(R)=0$, then we can talk about inverses of the form $1/n\in\mathbb{Q}$. 
  
  We do this as follows define $\tilde{n}\in R$ as the sum of $n$ 1's
  $$
  \tilde{n}=1 + \dots + 1
  $$
  Now we have for $a\in R$  
  $$
  \tilde{n}a = n\cdot a
  $$
  And by definition $\tilde{n}$ has an inverse $\tilde{n}^{-1}$ such that
  $$
  \tilde{n}\tilde{n}^{-1}a = n\cdot (1/n) \cdot a
  $$
  The corresponding number of $1$'s that are needed to get to $\hat{n}^{-1}$ is defined as $1/n$.  

* (*Fraleigh 24.10*) **Wedderburn's Theorem**: Every finite division ring is  a field. 
  
  Another way to say this is that there are no finite strictly skew fields.


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]