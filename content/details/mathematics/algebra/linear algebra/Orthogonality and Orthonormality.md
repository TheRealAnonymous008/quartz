* Let $V$ be an [[Inner Product Space|inner product space]]. A vector $x\in V$ is a **unit vector** if $||x||=1$. $x,y\in V$ are **orthogonal** if $\braket{x,y}=0$.
  
  A subset $S\subseteq V$ is **orthogonal** if any two distinct elements of $S$ are orthogonal
  
  A subset $S\subseteq V$ is **orthonormal** if $S$ is orthogonal and consists entirely of unit vectors.
	* If $S=\set{x_1,x_2,\dots}$ then $S$ is orthonormal if and only if  
	  $$
	  \braket{x_i,x_j} = \delta_{ij}
	  $$
	  Where $\delta_{ij}$ is the Kronecker delta. 

* (*Friedberg e6.1.10*) **Pythagorean Theorem Analogue** If $x,y$ are orthogonal elements of $V$ then
  $$
  ||x+y||^2 =||x||^2 + ||y||^2
  $$
* (*Friedberg e6.1.12*) Let $\set{x_1,\dots,x_k}$ be an orthogonal set in $V$ and $a_1,\dots, a_n\in F$. Then
  $$
  \left|\left|\sum_{i=1}^ka_ix_i\right|\right| = \sum_{i=1}^k |a_i|^2 ||x_i||^2
  $$

* (*Friedberg 6.3*) Let $V$ be an inner product space and let $S=\set{x_1,\dots,x_k}$ be an orthogonal set of nonzero vectors. If
  $$
  y = \sum_{i=1}^k a_i x_i
  $$
  Then $\forall j$
  $$
  a_j = \frac{\braket{y,x_j}}{||x_j||^2}
  $$
	* (*Friedberg 6.3.1*) If $S$ above is orthonormal, then 
	  $$
	  y=\sum_{i=1}^k \braket{y,x_i} x_i
	  $$
	* (*Friedberg 6.3.2*) Let $V$ be an inner product space. Let $S$ be an orthogonal set of nonzero vectors. Then $S$ is [[Linear Combination|linearly independent]]. 


 * (*Friedberg 6.4*) Let $V$ be an inner product space and let $S=\set{y_1,\dots,y_n}$ be a linearly independent subset of $V$. Define $S'=\set{x_1,\dots,x_n}$ where $x_1=y_1$ and 
   $$
   x_k=y_k - \sum_{j=1}^{k-1} \frac{\braket{y_k,x_j}}{||x_j||^2} x_j
   $$
   For $2\le k \le n$
   
   Then $S'$ is an orthogonal set of nonzero vectors such that $\text{span}(S')=\text{span}(S)$.
   
   This construction is called the **Gram-Schmidt Orthogonalization Process**. 
	* An orthonormal basis can then be obtained by applying the Gram-Schmidt Orthogonalization process and dividing by the norm of the vectors.

* (*Friedberg 6.5*) Let $V$ be a finite dimensional inner product space. Then $V$ has an orthonormal basis $\beta$. Furthermore, if $\beta=\set{x_1,\dots,x_n}$ and $x\in V$. Then 
  $$
  x=\sum_{i=1}^n \braket{x,x_i} x_i
  $$
	* (*Friedberg 6.5.1*)  Let $\beta$ be an orthonormal basis and $T$ a [[Linear Transformation|linear operator]] on $V$ and let $A=[T]_\beta$. Then
	  $$
	  A_{ij} = \braket{T(x_j), x_i}
	  $$
* Let $\beta$ be an orthonormal subset of an inner product space $V$ and $x\in V$. The **Fourier coefficients** of $x$ relative to $\beta$ are the scalars $\braket{x,y}$ where $y\in\beta$.

* Let $V$ be an inner product space and $S\subseteq V$. Then $S^\perp$ is the **orthogonal complement** of $S$ defined as the set of all vectors in $V$ orthogonal to every vector in $S$. That is 
  $$
  S^\perp = \set{x\in V \mid \braket{x,y} =0 \forall y\in S}.
  $$
	* $S^\perp$ is a [[Vector Subspace|subspace]] for any $S\subseteq V$. 

* (*Friedberg 6.6*) Let $W$ be a finite dimensional subspace of an inner product space $V$.  If $\set{x_1,\dots, x_k}$ is an orthonormal basis of $W$ and $y\in V$ then
  $$
  y= \sum_{i=1}^k \braket{y,x_i} x_i + z
  $$
  Where $z\in W^\perp$. This representation of $y$ is unique. That is $z\in W^\perp$ is unique.
	* (*Friedberg 6.6.1*) 
	  $$
	  y_\perp = \sum_{i=1}^k \braket{y,x_i} x_i
	  $$
	  Is the unique vector in $W$ that is "closest" to $y$. That is, if $u\in W$ then 
	  $$
	  ||y-u||\ge ||y-y_\perp||
	  $$
	  And also $y-y_\perp \in W^\perp$.
	  
	  We call $y_\perp$ the **orthogonal projection** of $y$ on $W$
	* (*Friedberg e6.2.6*) If $x\notin W$ there exists $y\in V$ such that $y\in W^\perp$ but $\braket{x,y}\ne 0$. 
		* *Intuition*: Use (*Friedberg 6.6*). We have that $x=x_\perp + y$ assuming $x\notin W$ and by the fact that $y \ne 0$ (otherwise $x\in W$), we have
		  $$
		  \braket{x,y} = \braket{x_\perp + y,y} = \braket{x_\perp, y} + \braket{y,y} > 0
		  $$ 

* (*Friedberg 6.7*) Suppose that $S=\set{x_1,\dots,x_k}$ is an orthonormal set in an $n$-dimensional inner product space $V$. Then
	* $S$ can be extended to an orthonormal basis for $V$ using additional elements $S_\perp = \set{x_{k+1},\cdots,x_n}$ 
	* If $W=\text{span}(S)$ then the set $S_\perp$ is an orthonormal basis for $W^\perp$
	* If $W\le V$, then $\dim(V)=\dim(W) + \dim(W^\perp)$. In fact (*Fraleigh 6.2.12d*) $V=W\oplus W^\perp$ (see [[Vector Sum and Direct Sum|here]]). 

* (*Friedberg e6.2.11*) Let $W_1,W_2\le V$, where $V$ is an inner product space. Then
  $$
  \begin{split}
  (W_1+W_2)^\perp &=W_1^\perp \cap W_2^\perp \\
  (W_1\cap W_2)^\perp &= W_1^\perp + W_2^\perp
  \end{split}
  $$

* (*Friedberg e6.2.12*) Let $V$ be an inner product space, $S,S_0\subseteq V$ and $W$ be  a finite dimensional subspace of $V$. We have
	* $S_0\subseteq S \implies S^\perp \subseteq S_0^\perp$ 
	* $S\subseteq (S^\perp)^\perp$ so that $\text{span}(S)\subseteq (S^\perp)^\perp$ 
	* $W=(W^\perp)^\perp$. 

* (*Friedberg e6.2.13a*) **Parseval's Identity**. Let $\set{x_1,\dots,x_n}$ be an orthonormal basis for $V$. For any $x,y\in V$ we have
  $$
  \braket{x,y} = \sum_{i=1}^n\braket{x,x_i} \overline{\braket{y,x_i}}
  $$
* (*Friedberg e6.2.14*) **Bessel's Inequality** Let $V$ be an inner product space and $S=\set{x_1,\dots,x_n}$ be any orthonormal subset of $V$. For any $x$ we have
  $$
  ||x||^2 \ge \sum_{i=1}^n |\braket{x,x_i}| ^2 
  $$ 

* Let $V$ be an inner product space and $T:V\to V$ be a [[Projection|projection]]. $T$ is an **orthogonal projection** if 
	* $R(T)^\perp = N(T)$
	* $N(T)^\perp = R(T)$

* *Orthogonal Projections are uniquely determined by their range*.
* (*Friedberg 6.23*) Let $V$ be an inner product space and $T$ be a linear operator on $V$. Then $T$ is an orthogonal projection if and only if
  $$
  T^2 = T= T^\ast 
  $$

# Geometric Interpretation
* Let $T$ be a linear operator on a finite-dimensional real inner product space $V$. $T$ is a **rotation** if $T$ is the identity on $V$ or if there exists a two dimensional subspace $W$ of $V$, an orthonormal basis $\beta=\set{x_1,x_2}$ for $W$ and a real number $\theta$ such that
  $$
  T\left(\begin{bmatrix}
  x_1 \\
  x_2
  \end{bmatrix}
  \right) = \begin{bmatrix}
  \cos\theta & \sin\theta \\
  -\sin\theta & \cos\theta
  \end{bmatrix}\begin{bmatrix}
  x_1 \\
  x_2
  \end{bmatrix}
  $$
  And $T(y)=y$ for all $y\in W^\perp$. 
  
  We refer to $W^\perp$ as the **axis of rotation**. $T$ is called a rotation of $W$ about $W^\perp$. 

* Let $T$ be a linear operator on a finite-dimensional real inner product space $V$. The operator $T$ is called a **reflection** if there exists a one-dimensional subspace $W$ of $V$ such that 
  $$
  T(x) = \begin{cases}
  -x & \text{if } x \in W \\ 
  x & \text{if } x \in W^\perp
  \end{cases}
  $$
  We say that $T$ is a reflection of $V$ about $W^\perp$.

* (*Friedberg 6.38*) Let $T$ be an orthogonal operator on a two dimensional real inner product space $V$. Then $T$ is *either a reflection or a rotation*.
  
  Also $T$ is a reflection if and only if the [[Determinant]] $\det(T)=1$
  $T$ is a rotation if and only if $\det(T)=1$. 
	* (*Friedberg e6.10.8*) No orthogonal operator can be both a rotation and a reflection.
* (*Friedberg 6.38.1*) Let $V$ be a two dimensional real inner product space. The [[Fundamental Constructs of Group Theory|composition]] of a reflection and a rotation on $V$ is a reflection on $V$. 
* (*Friedberg 6.39*) Let $T$ be an orthogonal operator on a nonzero finite dimensional real inner product space $V$. Then there exists a collection of pairwise orthogonal $T$-[[Invariant Subspace|invariant subspaces]] $\set{W_1,\dots, W_n}$ of $V$ such that
	* $1\le \dim (W_i)\le 2$ 
	* $V=W_1 \oplus W_2 \oplus \dots\oplus W_n$ 
	* The restriction of $T$ to $W_i$ is either a rotation or a reflection. 
	* (*Friedberg 6.40*) 
		* The number of $i$'s for which $T_{W_i}$ is a reflection is even or odd according to whether $\det(T)=1$ or $\det(T)=-1$.
		* It is always possible to decompose $V$ as shown so that the number of $i$'s for which $T_{W_i}$ is a reflection is zero or one according to whether $\det(T)=1$ or $\det(T)=-1$. Also if $T_{W_i}$ is a reflection then $\dim(W_i)=1$. 

* (*Friedberg 6.40.1*) Let $T$ be an orthogonal operator on a finite dimensional real inner product space $V$. Then there exists a collection $\set{T_1,\dots,T_m}$ of orthogonal operators such that
	* Each $T_i$ is either a rotation or a reflection
	* For at most one $i$, $T_i$ is a reflection.
	* $T_iT_j=T_jT_i$
	* $T=T_1T_2\dots T_m$
	* $$
	  \det(T) = \begin{cases}
	  1 & \text{all } T_i's \text{ are rotations} \\ 
	  -1 & \text{otherwise}
	  \end{cases}
	  $$




# Links
* [[Linear Algebra by Friedberg Insel and Spence]]
* [[Geometry]]