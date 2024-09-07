* Not every [[Characteristic Polynomial|characteristic polynomial]] splits. However, we can still consider [[Factorization of Polynomials|factors]] of the characteristic polynomials to analyze the structure of these [[Linear Transformation|linear]] transformations.
* One canonical form is the **rational canonical form** for the linear operator $T$ on $V$. This involves an ordered basis $\beta$ for $V$ such that 
  $$
  [T]_\beta = \begin{bmatrix}
  C_1 & O & \cdots & O \\
  O & C_2 & \cdots & O \\
  \vdots & \vdots & \ddots & \vdots \\
  O & O & \cdots & C_r
  \end{bmatrix}
  $$
  Where each $C_i$ is the **companion matrix** of some polynomial $(\phi(t))^m$ where $\phi(t)$ is a monic irreducible divisor of the characteristic polynomial of $T$ and $m\in \mathbb{Z}^+$
  
  A companion matrix for
  $$
  h(x) = a_0 + a_1t + \dots + a_{k-1}t^{k-1} + t^k
  $$
  Is the matrix 
  $$
  \begin{bmatrix}
  0 & 0 & \cdots & 0 & -a_0 \\
  1 & 0 & \cdots & 0 & -a_1 \\
  0 & 1 & \cdots & 0 & -a_2 \\
  \vdots & \vdots & \ddots & \vdots & \vdots \\
  0 & 0 & \cdots & 1 & -a_{k-1} \\
  \end{bmatrix}
  $$
	* *Notation*: We order every rational canonical basis so that all $T$-cyclic bases associated with the same irreducible monic divisor of the characteristic polynomial are grouped together.
	  
	  Within each grouping, the $T$-cyclic bases are in order of decreasing size. 
	* Let $r_i$ be the number of dots in the $i$-th row of the corresponding dot diagram and $p_i$ the number of dots in the $i$-th column
	* For matrices, the definition is similar. The rational canonical form of $A\in M_{n\times n}(F)$ is the rational canonical form of the linear operator $L_A : F^n \to F^n$.  The accompanying basis is the rational canonical basis of $A$
	* *The rational canonical basis is not unique*. 


* Let $T$ be a linear operator on a finite dimensional vector space $V$ with characteristic polynomial
  $$
  f(t)=(-1)^n (\phi_1(t))^{n_1} \dots (\phi_k(t))^{n_k}
  $$
  Where the $\phi_i(t)$'s are distinct irreducible monic polynomials, each $n_i\in\mathbb{Z}^+$. 
  
  The **generalized eigenspace** corresponding to $\phi_i$ is defined
  $$
  K_{\phi_i} = \set{x\in V \mid (\phi_i(T)^p (x) = 0, \ \ \ p \in \mathbb{Z}^+)}
  $$

* (*Friedberg Lem.7.15*) Let $T$ be a linear operator on a finite dimensional vector space $V$ and let $x$ be a nonzero vector in $V$ and suppose that the $T$-[[Minimal Polynomial|annihilator]] of $x$ is of the form $(\phi(t))^n$ for some irreducible monic polynomial $\phi(t)$. Then $\phi(t)$ divides the minimal polynomial of $T$ and so does $x\in K_{\phi}$.

* (*Friedberg 7.16*) Let $T$ be a linear operator on a finite dimensional vector space $V$ and $\beta$ an ordered basis for $V$. Then $\beta$ is a rational canonical basis of $T$ if and only if $\beta$ is the disjoint union of $T$-[[Invariant Subspace|cyclic]] bass $B_{x_i}(T)$ where each $x_i\in K_{\phi}$ for some irreducible monic divisor $\phi(t)$ of the characteristic polynomial of $T$. 

* (*Friedberg 7.17*) Let $T$ be a linear operator on a finite dimensional vector space $V$ and let
  $$
  p(t) = (\phi_1(t))^{m_1} \dots (\phi_k(t))^{m_k}
  $$
  Be the minimal polynomial of $T$ where the $\phi_i(t)$'s are distinct irreducible monic factors of $p(t)$ and the $m_i$'s are positive integers. Then
	* For each $i$, $K_{\phi_i}$ is a nontrivial $T$-invariant subspace of $V$.
	* For $i\ne j$, $K_{\phi_i} \cap K_{\phi_j}=\emptyset$ 
	* For $i\ne j$, $K_{\phi_i}$ is invariant under $\phi_j(T)$ and the restriction of $\phi_j(T)$ to $K_{\phi_i}$ is one-to-one.
	* For each $i$ $K_{\phi_i}=N((\phi_i(t))^{m_i})$ 

* (*Friedberg Lem.7.18*) Let $T$ be a linear operator on a finite dimensional vector space $V$ and let $\phi_1,\dots, \phi_k$ be the distinct irreducible monic divisors of the minimal polynomial of $T$. Let $x_i\in K_{\phi_i}$ such that
  $$
  x_1 + x_2 + \dots + x_k = 0
  $$
  Then $x_i=0$ for all $i$.

* (*Friedberg 7.18*) Suppose that $T$ is a linear operator on a finite dimensional vector space $V$. Let $\phi_1, \phi_2, \dots, \phi_k$ be distinct irreducible monic divisors of the minimal polynomial of $T$ and for each $i$, let $S_i$ be a linearly independent subset of $K_{\phi_i}$. Then $S_i\cap S_j = \emptyset$ for $i\ne j$ and 
  $$
  S = \bigcup_{i=1}^k S_i
  $$
  Is a [[Linear Combination|linearly independent]] subset of $V$.

* (*Friedberg 7.19*) Let $x_1,\dots, x_k$ be distinct vectors in $K_\phi$ such that 
  $$
  S_1 = B_{x_1} (T) \cup \dots \cup B_{x_k} (T)
  $$
  is linearly independent. For each $i$, let $z_i$ be a vector in $V$ such that $\phi(T)(z_i)=x_i$. Then
  $$
  S_2 = B_{z_1} (T) \cup \dots \cup B_{x_k}(T) 
  $$
  is also linearly independent. 

* (*Friedberg Lem.7.20*) Let $W$ be a $T$-invariant subspace of $K_\phi$ and $\beta$ a basis for $W$. Then
	* $\forall x \in N(\phi(T))$ if $x\notin W$ then $\beta \cup B_x(T)$ is linearly independent.
	* For some $z_1,\dots,z_s \in N(\phi(T))$, $\beta$ can be extended to a linearly independent set
	  $$
	  \beta' = \beta \cup B_{z_1}(T) \cup \dots \cup B_{z_s}(T)
	  $$
	  such that $N(\phi(T)) \subseteq \text{span}(\beta')$

* (*Friedberg 7.20*) If the minimal polynomial of $T$ is of the form $p(t)=(\phi(t))^m$ then $T$ has a rational canonical basis.
* (*Friedberg 7.20.1*)  $K_\phi$ has a basis consisting of a union of $T$-cyclic basis 
	* *Intuition*: Apply (*Friedberg 7.20*) to the restriction of $T$ to $K_\phi$

* (*Friedberg 7.21*) Every linear operator on a finite dimensional vector space has a rational canonical basis, and hence a rational canonical form.
* (*Friedberg 7.22*) Let $T$ be a linear operator on an $n$-dimensional vector space $V$ with characteristic polynomial
  $$
  f(t) = (-1)^n (\phi_1(t))^n \dots (\phi_k(t))^{n_k}
  $$
  where the $\phi_i(t)$'s are distinct irreducible monic polynomials and the $n_i$'s are positive integers. Then
	* For each $i$, $\phi_i(t)$ divides the minimal polynomial of $T$
	* For each $i$, $\dim(K_{\phi_i})= n_i \deg(\phi(t))$ 
	* If $\beta$ is a rational canonical basis for $V$ then for each $i$, $\beta\cap K_{\phi_i}$ is a basis for $K_{\phi_i}$ 
	* If $S_i$ is a basis for $K_{\phi_i}$ then $S=\cup_{i=1=}^k S_i$ is a basis for $V$. In particular, if each $S_i$ is a disjoint union of $T$-cyclic bases, then $S$ is a rational canonical basis for $T$. 

* (*Friedberg 7.23*) Let $T$ be a linear operator on a finite dimensional vector space $V$. Let $\phi(t)$ be an irreducible monic divisor of the characteristic polynomial of $T$ of degree $d$. Then
  $$
  r_i = \begin{cases}
  \frac{1}{d} [\dim(V) - \text{rank}(\phi(T))] & \text{for } i = 1 \\
  \frac{1}{d} [\text{rank}((\phi(T))^{i-1}) - \text{rank}((\phi(T))^i)] & \text{for } i > 1 \\ 
  \end{cases}
  $$

* (*Friedberg Lem.7.23.1*) Let $a$ be the total number of dots in the dot diagram for $\phi(t)$. Then 
  $$
  a\deg(\phi(t)) = \dim(K_\phi)
  $$
  also for any $i\le p_1$
  $$
  \text{nullity}((\phi(T))^{i}) = \deg(\phi) (r_1 + \dots + r_i)
  $$
* (*Friedberg 7.23.1*) The rational canonical form of a linear operator is unique up to the arrangement of the irreducible monic divisors of the characteristic polynomial.

* (*Friedberg 7.24*) Let $T$ be a linear operator on an $n$-dimensional vector space $V$ with characteristic polynomial
  $$
  f(t) = (-1)^n (\phi_1(t) ^{m_1}) \dots (\phi_k(t))^{n_k}
  $$
  Where the $\phi_i(t)$'s are distinct irreducible monic polynomials and each $n_i\in\mathbb{Z}^+$. Then
	* $V=K_{\phi_1} \oplus \dots \oplus K_{\phi_k}$ (see [[Vector Sum and Direct Sum|here]])
	* If $T_i$ is the restriction of $T$ to $K_{\phi_i}$ and $C_i$ is the rational canonical form of $T_i$ then 
	  $$
	  C_1 \oplus \dots \oplus C_k
	  $$
	  Is the rational canonical form of $T$.

* (*Friedberg 7.25*) Let $T$ be a linear operator on a finite dimensional vector space $V$, then $V$ is a direct sum of $T$-cyclic subspaces $C_{x_i}(T)$ where each $x_i\in K_{\phi}$ for some irreducible monic divisor $\phi(t)$ of the characteristic polynomial of $T$.

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]