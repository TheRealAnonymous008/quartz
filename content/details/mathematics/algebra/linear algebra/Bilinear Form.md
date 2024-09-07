* Let $V$ be a [[Vector Space|vector space]] over $F$. A function $H:V\times V\to F$ is called a **bilinear form** on $V$ if $H$ is [[Linear Transformation|linear]] in each variable when the other variable is held fixed. That is $\forall x_1,x_2,y_1,y_2,x,y\in V$ and $\forall a\in F$
  
  $$
  \begin{split}
  H(ax_1 + x_2 , y) &= aH(x_1,y) + H(x_2, y) \\ 
  H(x,ay_1 + y_2 ) &= aH(x,y_1) + H(x,y_2)
  \end{split}
  $$
  The set of all bilinear forms on $V$ is denoted $\mathcal{B}(V)$

* (*Friedberg e6.7.2*) For any bilinear form $H\in \mathcal{B}(V)$ 
	* If for any $x\in V$ the functions $L_x,R_x:V\to F$ are defined by
	  $$
	  \begin{split}
	  L_x(y) &= H(x,y) \\
	  R_x(y) &= H(y,x) 
	  \end{split}
	  $$
	  Then $L_x$ and $R_x$ are linear
	* $\forall x\in V \ \ \ H(0,x)=H(x,0)=0$
	* If $x,y,z,w\in V$ then 
	  $$
	  H(x+y,z+w) = H(x,z) + H(x,w) + H(y,z) + H(y,w)
	  $$
	* If $J:V\times V\to F$ is defined by $J(x,y) = H(y,x)$, then $J$ is a bilinear form.

* The **sum** and **scalar product** of bilinear forms are defined as follows
  $$
  \begin{split}
  (H_1 + H_2) (x,y) &= H_1(x,y) + H_2(x,y) \\
  (aH_1) (x,y) &= a(H_1(x,y))
  \end{split}
  $$
* (*Friedberg 6.25*)  For any vector space $V$, $\mathcal{B}(V)$ is a vector space with the sum and scalar product of bilinear forms as addition and scalar multiplication

* The **Matrix Representation** of a bilinear form with respect to basis $\beta$ can be defined as follows. Let $A\in M_{n\times n}(F)$ be a [[Matrix|matrix]] and $\beta = \set{x_1,\dots,x_n}$ be an ordered [[Linear Combination|basis]]. We associate with $A$ to $H\in \mathcal{B}(V)$ by defining
  $$
  A_{ij} = H(x_i, x_j)
  $$
  We denote this as
  $$
  \psi_\beta(H) = A
  $$

* (*Friedberg 6.26*) For any $n$-dimensional vector space $V$ over field $F$ and any basis $\beta$ for $V$. $\psi_\beta$ is a vector space isomorphism. 
* (*Friedberg 6.26.1*) $\dim(\mathcal{B}(V))=\dim(V)^2$
* (*Friedberg 6.26.2*) Let $V$ be an $n$-dimensional vector space over the field $F$ with basis $\beta$. If $H\in \mathcal{B}(V)$ and $A\in M_{n\times n}(F)$, then 
  $$
  \psi_\beta (H) =A \iff H(x,y) = [\phi_\beta (x)]^T A[\phi_\beta(y)]
  $$
* (*Friedberg 6.26.3*) For any field $F$, positive integer $n$ and $H\in \mathcal{B}(F^n)$, there exists a unique matrix $A\in M_{n\times n}(F)$ where $\beta$ is the standard ordered basis for $F^n$ such that
  $$
  H(x,y)=x^T Ay
  $$
  In fact $A=\psi_\beta(H)$

* Two matrices, $A,B\in M_{n\times n}(F)$ are said to be **congruent** if there exists an [[Matrix Inversion|invertible]] matrix $Q\in M_{n\times n}(F)$ such that 
  $$
  Q^TAQ = B
  $$
	* (*Friedberg e6.7.11*) Congruence defines an [[Relation|equivalence relation]]. 

* (*Friedberg 6.27*) Let $V$ be a finite dimensional vector space with bases $\beta=\set{x_1,\dots,x_n}$ and $\gamma=\set{\gamma_1,\dots,\gamma_n}$ and let $Q$ be the change of [[Vector Coordinate System|coordinate]] matrix changing $\gamma$-coordinates to $\beta$-coordinates. Then, for any $H\in \mathcal{B}(V)$, 
  $$
  \psi_\gamma (H)= Q^T\gamma_\beta (H) Q
  $$
  In particular, $\psi_\beta(H)$ and $\psi_\gamma(H)$ are congruent.
* (*Friedberg 6.27.1*) Let $V$ be an $n$-dimensional vector space with basis $\beta=\set{x_1\dots,x_n}$. Suppose that $H\in \mathcal{B}(V)$ and $B\in M_{n\times n}(F)$. 
  
  If $B$ is congruent to $\psi_\beta(H)$, then there exists a basis $\gamma$ for $V$ such that $\psi_\gamma(H)=B$. 
  
  In fact if $B=Q^T\psi_\beta(H)Q$ for an invertible matrix $Q$, then $Q$ changes $\gamma$-coordinates into $\beta$-coordinates.
	* *Intuition*: Apply a change of coordinate matrix to (*Friedberg 6.26.2*) 

* (*Friedberg Lem.6.29*) Let $H$ be a nontrivial symmetric bilinear form on a vector space over a field $F$ not of [[Fundamental Constructs of Ring Theory|characteristic]] $2$ then there exists an element $x\in V$ such that $H(x,x)\ne 0$. 
# Symmetric Bilinear Forms
* A bilinear form $H$ over a vector space $V$ is **symmetric** if $\forall x,y\in V$ 
  $$
  H(x,y) = H(y,x)
  $$
* (*Friedberg 6.28*) Let $V$ be a finite-dimensional vector space. For $H\in \mathcal{B}(V)$ the following are equivalent
	* $H$ is symmetric.
	* For any basis $\gamma$ for $V$, $\psi_\gamma(H)$ is a symmetric matrix.
	* There exists a basis $\beta$ for $V$ such that $\psi_\beta(H)$ is a symmetric matrix.
* (*Friedberg 6.28.1*) Let $V$ be a finite dimensional vector space. For any $H\in \mathcal{B}(V)$, if $H$ is diagonalizable, then $H$ is symmetric.

* A bilinear form $H$ on a finite dimensional vector space $V$ is called **[[Matrix Diagonalization|diagonalizable]]** if there exists a basis $\beta$ for $V$ such that $\psi_\beta(H)$ is a diagonal matrix

* (*Friedberg 6.29*) Let $V$ be a finite dimensional vector space over a field $F$ of characteristic two. Then every symmetric bilinear form on $V$ is diagonalizable.
* (*Friedberg 6.29.1*) Let $F$ be a field that is not of characteristic two. If $A\in M_{n\times n}(F)$ is a symmetric matrix, then $A$ is congruent to a diagonal  matrix.
* (*Friedberg 6.30*) Let $V$ be a finite dimensional real [[Inner Product Space|inner product space]] and $H$ a symmetric bilinear form on $V$. Then there exists an [[Orthogonality and Orthonormality|orthonormal]] basis $\beta$ for $V$ such that $\psi_\beta(H)$ is a diagonal matrix

# Sylvester's Laws of Innertia
* Any two matrix representations of a bilinear form have the same [[Dimension Theorem|rank]]. Thus, the **rank** of a bilinear form is the rank of any of its representation.
* **Sylvester's Law of Inertia** states the following: Let $H$ be a symmetric bilinear form on a finite dimensional real vector space $V$. Then the number of positive diagonal entries and the number of negative diagonal entries of any diagonal representation of $H$ are both independent of the diagonal representation.
	* *Proof*: Suppose we have diagonal representations with respect to $\beta$ and $\gamma$ with $p$ and $q$ positive entries respectively. Without loss of generality, assume $p<q$. Let $r=\text{rank}(H)$ and $n=\dim(V)$. We have
	  $$
	  \begin{split}
	  \beta &= \set{x_1,\dots,x_p,\dots,x_r,\dots,x_n} \\
	  \gamma &= \set{y_1,\dots,y_q,\dots,y_r,\dots,y_n}
	  \end{split}
	  $$
	  Define $L:V\to \mathbb{R}^{r+p-q}$ be defined by
	  $$
	  L(x) = (H(x,x_1), \dots,H(x,x_p), H(x,y_{q+1}), \dots, H(x,y_r))
	  $$
	  Clearly $L$ is linear and $\text{rank}(L)\le p + r - q$ and therefore $\text{nullity}(L)\ge n-p-r+q>n-r$. 
	  
	  Choose $x_0\notin \text{span}(\set{x_{r+1},\dots,x_n})$ such that $x_0\in N(L)$.  Thus
	  $H(x_0,x_i)=0$ for $i\le p$ and $H(x_0,y_i)=0$ for $q<i\le r$. Represent $x$ in terms of the bases $\beta$ and $\gamma$. That is $x_0=\sum_{j=1}^n a_jx_j = \sum_{j=1}^nb_jy_j$ 
	  
	  Note that for $i\le p$, we have $H(x_i,x_i)>0$ by our stipulation. Hence $a_i=0$ for all such $i$. Similarly $b_i=0$ whenever $q+1\le i \le r$ Thus, $a_i\ne 0$ for some $p<i\le r$ since $x_0\notin \text{span}(\set{x_{r+1},\dots,x_n})$. 
	  
	  Now  consider $H(x_0,x_0)$ and compute it using both representations of $x_0$. We end up with the claim that both $H(x_0,x_0)<0$ and $H(x_0,x_0)>0$, a contradiction. Therefore $p=q$.

* The **index** is the number of positive diagonal entries of a diagonal representation of a symmetric bilinear form on a real vector space. The same term is used for a diagonal matrices congruent to a real symmetric matrix
* The **signature** of the form is the difference between positive and negative diagonal entries in a diagonal representation of a symmetric bilinear form. The same term is used for a diagonal matrices congruent to a real symmetric matrix

* *Sylvester's Law of Inertia states that rank, index, and signature are invariants of a bilinear form (and diagonal matrices congruent to a real symmetric matrix)*.

* **Sylvester's Law of Inertia for Matrices**. Let $A$ be a symmetric matrix. Then, the number of positive diagonal entries and the number of negative diagonal entries of any diagonal matrix congruent to $A$ is independent of the choice of the diagonal matrix.

* **Sylvester's Law of Inertia** (*Cor.2*) Two real symmetric $n\times n$ matrices are congruent if and only if they have the same index, signature, and rank.

* In the theory of real symmetric matrices, we define a **canonical form** matrix $J_{pr}$
  $$
  J_{pr} = 
  \begin{bmatrix}
  I_p & O & O \\
  O & -I_{r-p} & O \\
O &O &O 
  \end{bmatrix}
  $$
	* **Sylvester's Law of Inertia** (*Cor.2*) A real symmetric matrix $A$ has index $p$ and rank $r$ if and only if $A$ is congruent to $J_{pr}$. 

# Links
* [[Linear Algebra by Friedberg Insel and Spence]]