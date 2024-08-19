# Extension from Elementary Algebra
* We say $R[x]$ to mean the set of all polynomials with coefficients in the [[Fundamental Constructs of Ring Theory|ring]] $R$.  $R[x]$ is a ring called the **Polynomial Ring** where addition and multiplication are defined similarly for polynomials.
  
  More formally, a **Polynomial** $f(x)$ with coefficients in $R$ is an infinite formal sum 
  $$
  \sum_{i=0}^\infty a_ix^i  = a_0 + a_1x+\dots +a_nx^n+\dots
  $$
  Where $a_i\in R$ and $a_i=0$ for all but a finite number of values of $i$. We refer to $a_i$ as the **coefficients**. We refer to $x$ as the **indeterminate**.
  
  If for some $i\ge 0$, $a_i\ne 0$, the largest such $i$ is the **degree** of $f(x)$ denoted $\deg f(x)$.
  
  If all $a_i=0$, then $\deg f(x)=-\infty$. 
  
  All polynomials are written as they would be written following the conventions of elementary algebra.

* Let $f(x)=a_0+a_1x+\dots +a_nx^n + \dots$ and $g(x) = b_0 ++b_1 + \dots + b_nx^n + \dots$. Then 
  
  Polynomial addition is defined as 
  $$
  f(x) + g(x) = c_0 + c_1x + \dots + c_nx^n + \dots
  $$
  Where $c_n=a_n + b_n$
  
  Polynomial multiplication is defined as
  $$
  f(x)\cdot g(x) = d_0+ d_ix + \dots + d_nx^n +\dots 
  $$
  Where $d_n = \sum_{i=0}^n a_i b_{n-i}$ 
* More generally, if we have indeterminates $x_1,\dots,x_n$, we denote the polynomial ring in these indeterminates as $R[x_1,\dots,x_n]$.

* (*Fraleigh 22.2*) $R[x]$ is a ring under polynomial addition and multiplication. If $R$ is [[Commutative Ring|commutative]] then so it $R[x]$. If $R$ has a [[Division Ring and Rings with Unity|unity]] $1\ne 0$, then $1$ is also the unity in ring $R[x]$. 
* (*Fraleigh e22.24* ) If $D$ is an [[Integral Domain]] then so is $D[x]$


* (*Fraleigh 22.4*) **The Evaluation Homomorphisms for Field Theory**  [^eval_hom] Let $F$ be a subfield of [[Field]] $E$ and $\alpha\in E$. Let $x$ be the indeterminate. The map $\phi_\alpha: F[x]\to E$ defined by
  $$
  \phi_a(a_0 + a_1x + \dots + a_nx^n) = a_0+a_1\alpha + \dots + a_n\alpha^n
  $$
  For $(a_0+\dots +a_nx^n)\in F[x]$ is a [[Ring Homomorphism|homomorphism]] of $F[x]$ into $E$.
  
  Also $\phi_\alpha(x)=\alpha$ and $\phi_\alpha$ maps $F$ isomorphically by the identity map : $\phi_\alpha(a) = a$ $\forall a\in F$ .
  
  We refer to $\phi_\alpha$ as an **evaluation** at $\alpha$
	* *Intuition*: This generalizes the elementary algebra notion of substituting $\alpha$ in the polynomial and evaluating

* Let $F$ be a subfield of $E$ and $\alpha\in E$   Let $f(x)=a_0+a_1x + \dots + a_nx^n\in F[x]$ and $\phi_\alpha:F[x]\to E$ be the evaluation homomorphism. 
  
  Let $f(\alpha)$ denote
  $$
  f(\alpha) = \phi_\alpha(f(x)) = a_0 + a_1\alpha + \dots + a_n \alpha^n
  $$
  If $f(\alpha)=0$, then $\alpha$ is a **zero** of $f(x)$. 

[^eval_hom]: This theorem holds for commutative rings as well. 

# Factorization 
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]