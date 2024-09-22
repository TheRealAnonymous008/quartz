* Let $S$ be a finite subset of $F[x]$. The **algebraic variety** $V(S)$ in $F^n$ *is the set of all common zeros* of $F^n$ of the polynomials in $S$. 

* Let $I$ be an ideal in a [[Commutative Ring]] $R$ with [[Ring with Unity|unity]]. A subset $\set{b_1,\dots,b_r}\subseteq I$ is a **basis** for $I$ if $\braket{b_1,b_2,\dots,b_r}$

* (*Fraleigh 28.4*) Let $f_1,\dots,f_r\in F[x]$. The set of common zeros in $F^n$ of the polynomials $f_i$ for $i=1,\dots,r$ is the same as the set of common zeros in $F^n$ of all the polynomials in the entire ideal $I=\braket{f_1,\dots,f_r}$ 

* (*Fraleigh 28.5*) **Hilbert Basis Theorem** Every [[Ideal]] in $F[x_1,\dots,x_n]$ has a finite basis. 

* (*Fraleigh 28.6*) Let $f(x),g(x),q(x),r(x)\in F[x]$ such that $f(x)=g(x)q(x)+r(x)$. If $f(x)$ and $g(x)$ are two members of a basis for an ideal $I$ of $F[x]$ then [[Matroid Theory|replacement]] of $f(x)$ by $r(x)$ in the basis still yields a basis for $I$.

* An ordering for the set of power products of $F[x]$ can be defined by having
  $$
  P_i\text{ divides } P_j \implies P_i < P_j
  $$ 
* A set $\set{g_1,\dots,g_r}$ of nonzero polynomials in $F[x_1,\dots,x_n]$ with term ordering $<$ is a **Groebner basis** for the ideal $I=\braket{g_1,\dots,g_r}$ if and only if for each nonzero $f\in I$, there exists some $i$ where $1\le i \le r$ such that $\text{1p}(g_i)$ divides $\text{1p}(f)$,. 


* (*Fraleigh 28.12*) Denote by $S(f,g)$ the polynomial obtained as follows $f,g\in F[x]$. First, multiply them by $\text{lcm}(\text{1p}(f), \text{1p}(g))$. Then add or subtract with suitable coefficients from $F$ so that cancellation results.
  
  A basis $G=\set{g_1,\dots,g_r}$ is a Groebner basis for the ideal $\braket{g_1,\dots,g_r}$ if and only if for all $i\ne j$, the polynomial $S(g_i,g_j)$ can be reduced to zero repeatedly dividing remainders by elements of $G$ as in the division algorithm.

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]
* [[Polynomial Ring]]