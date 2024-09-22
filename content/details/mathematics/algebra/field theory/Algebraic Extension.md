* An [[Extension Field and Polynomials|extension field]] $E$ of field $F$ is an **algebraic extension** of $F$ if every element in $E$ is algebraic over $F$.
* If an extension field $E$ of a field $F$ is of finite dimension $n$ as a [[Vector Space|vector space]] over $F$, then $E$ is a **finite extension of degree $n$ over $F$**. The degree $n$ of $E$ over $F$ is denoted $[E:F]$  

* (*Fraleigh 31.3*) A finite extension field $E$ of a field $F$ is an algebraic extension of $F$.
	* *Proof*: Take $\alpha \in E$. The set $1,\alpha,\dots, \alpha^n$ forms a [[Linear Combination|linearly dependent set]]. Their linear combination gives a nonzero polynomial that evaluates to $0$. Therefore $\alpha$ is algebraic over $F$.

* (*Fraleigh 31.4*) If $E$ is a finite extension field of $F$ and $K$ is a finite extension field of $E$, then $K$ is a finite extension of $F$ and
  $$
  [K:F] = [K:E] [E:F]
  $$
  [^31.4]
  
  (*Fraleigh 31.6*) By induction if we have fields $F_i, i =1,\dots,r$ such that $F_{i+1}$  is a finite extension of $F_i$, then $F_r$ is a finite extension of $F_1$ and
  $$
  [F_r:F_1] = [F_r: F_{r-1}] [F_{r-1} : F_{r-2}] \dots [F_2 : F_1]
  $$
	* *Intuition*: If $\alpha=\set{\alpha_1,\dots, \alpha_n}$ is a basis for $K$ over $E$ $\beta = \set{\beta_1,\dots,\beta_m}$ is a basis for $E$ over $F$. Then, $\gamma=\set{\alpha_i\beta_j \mid i \le n, j \le m}$ is a basis for $K$ over $F$. 

	* (*Fraleigh 31.7*) If $E$ is an extension field of $F$, $\alpha \in E$ is algebraic over $F$ and $\beta\in F(a)$, then  $\deg(\beta,F)$ divides $\deg(\alpha, F)$

[^31.4]: Note the analogy with [[Subgroup|Lagrange's Theorem]] and *Fraleigh 10.14* in [[Cosets, Group Indices|cosets]].

* (*Fraleigh 31.11*) Let $E$ be an algebraic extension of a field $F$. Then there exists a finite number of elements $\alpha_1,\dots,\alpha_n\in E$ such that $E=F(\alpha_1,\dots,\alpha_n)$ if and only if  $E$ is a finite-dimensional vector space over $F$. That is, if and only if $E$ is a finite extension of $F$
	* *Proof*: In the forward case,  $F(\alpha_1)$ is algebraic over $F$. $F(\alpha_2,\alpha_1)$ is algebraic over $F(\alpha_1)$ and so on. Now get
	  $$
	  [E:F] = [F(\alpha_1)  : F] \ [F(\alpha_1,\alpha_2) : F(\alpha_1)] \cdots [E : F(\alpha_1,\dots, \alpha_{n-1})]
	  $$
	  Which is finite.
	  
	  Conversely, if $E$ is a finite algebraic extension of $F$, we can keep adding elements $\alpha_1,\dots,\alpha_n$ where $[E:F]=n$. We do it such that $\alpha_1\notin F, \alpha_2\notin F(\alpha_1), \dots , \alpha_n \notin F(\alpha_1)\dots(\alpha_{n-1})$  This construction gives us 
	  
	  $$
	  E= F(\alpha_1)(\alpha_2)\dots(\alpha_n) = F(\alpha_1,\dots,\alpha_n)
	  $$

* (*Fraleigh 31.23*) If $E$ is a finite extension of field $F$ and $[E:F]$ is a [[Number Theory|prime]] number, then $E$ is a simple extension of $F$. Thus $\forall a\in E-F, E=F(\alpha)$
	* *Proof*: We have for any $\alpha$
	  $$
	  [E:F] = [E:F(\alpha)] [F(\alpha) : F]
	  $$
	  Note that the factors of a prime $p$ are $1$ and $p$.
	  Clearly $[F(\alpha): F)\ne 1$ since $\alpha\notin F$, Therefore $[F(\alpha):F]=p$ since $[E:F]=p$. Consequently, $[E:F(\alpha)] = 1$ and thus $E=F(\alpha)$


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]