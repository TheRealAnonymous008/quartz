* Assuming it exists, $1$ is the multiplicative identity (also called **unity**). *The multiplicative identity need not exist.*
	* The following is immediately true
	  $$
	  (m\cdot 1) (n\cdot 1) = (mn) \cdot 1
	  $$
	* (*Fraleigh 19.15*) Let $R$ be a ring with unity. If $n\cdot 1 \ne 0$ $\forall n\in \mathbb{Z}^+$ then $\text{char}(R) = 0$. 
	  
	  Otherwise, if $\exists n\in\mathbb{Z}^+$ such that $n\cdot 1 = 0$, then the smallest such $n$ is the characteristic of $R$. 
		* We may redefine the characteristic as the number of times we need to add the multiplicative identity to get the additive identity.

* An element $u\in R$ is a **unit** of $R$ if it has a multiplicative inverse. That is $u^{-1}$ is defined so that
  $$
  u\cdot u^{-1} = 1
  $$

* If every nonzero element of $R$ is a unit, then $R$ is a **division [[Fundamental Constructs of Ring Theory|ring]]**. 
	* If it is commutative, we call it a [[Field]].
	* Otherwise we call it a **strictly skew field**.

* (*Fraleigh e18.37*) If $U$ is the collection of all units in ring $(R,+,\cdot)$ with unity. Then $(U,\cdot)$ is a [[Fundamental Constructs of Group Theory|group]]. 
	* The set $G_n$ of nonzero elements of $\mathbb{Z}_n$ that are not $0$ [[Integral Domain|divisors]] forms a group under multiplication modulo $n$.

* (*Fraleigh e18.42*) The multiplicative inverse of a unit is unique.
* (*Fraleigh e19.23*) A division ring contains exactly two idempotent elements

* (*Fraleigh e19.30*) *Every $R$ can be enlarged to a ring $S$ with unity* having the same characteristic as $R$. We define $S$ as follows. 
  
  $$
  S = \begin{cases}
  R\times \mathbb{Z} & \text{ if } \text{char} (R) = 0 \\
  R\times \mathbb{Z}^n & \text{ if } \text{char}(R) = n
  \end{cases}
  $$
  Addition in $S$ is the same as addition in $R$
  
  Multiplication is defined as
  $$
  (r_1,n_1)(r_2,n_2) = (r_1r_2 + n_1\cdot r_2 + n_2\cdot r_1 + n_1r_)
  $$
  
  We can show the following
	* $S$ is a ring
	* $S$ has unity
	* $\text{char}(R)=\text{char}(S)$
	* $\phi:R\to S$ where $\phi(r)=(r,0)$ gives an isomorphism onto a subring of $S$.

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

* (*Fraleigh 26.3*) Let $\phi:R\to R'$ be a [[Ring Homomorphism]]. If $R$ has unity $1$, then $\phi(1)$ is unity for $\phi[R]$.
  
  In other words, rings with unity are still rings with unity under homomorphism.
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]