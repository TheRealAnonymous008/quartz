* Not every linear operator $T$ on $V$ is [[Matrix Diagonalization|diagonalizable]]. However, for any linear operator whose [[Characteristic Polynomial|characteristic polynomial]] splits, there exists an ordered [[Linear Combination|basis]] $\beta$ for $V$ such that 
  $$
  [T]_\beta = \begin{bmatrix}
  J_1 & O & \cdots & O \\
  O & J_2 & \cdots & O \\
  \vdots & \vdots & \ddots & \vdots \\
  O & O & \cdots & J_k
  \end{bmatrix}
  $$
  Where $J_i$ is a square matrix of the form $[\lambda_j]$ or of the form
  $$
  \begin{bmatrix}
  \lambda_j & 1 & 0 &\cdots & 0 & 0 \\ 
  1 & \lambda_j & 0 &\cdots & 0 & 0 \\
  \vdots & \vdots & \vdots & \ddots & \vdots & \vdots  \\
  0 & 0 & 0 & \cdots & \lambda_j & 0 \\
  0 & 0 & 0 & \cdots & 0 & \lambda_j \\
  \end{bmatrix}
  $$
  For some eigenvalue $\lambda_j$ of $T$. We call $J_i$ a **Jordan Block** of corresponding to $\lambda_j$. The matrix $[T]_\beta$ is called a **Jordan Canonical Form** of  $T$. $\beta$ is the **Jordan Canonical Basis**.
	* *Intuition*: If $T$ is not diagonalizable, there is a well-defined notion of "almost diagonalizable" (i.e., the Jordan Canonical Form) 
	* The Jordan Canonical Form of a matrix is defined similarly. That is, The Jordan canonical form of $A\in M_{n\times n}(F)$ is the Jordan canonical form of $L_A$. 

*  Let $T$ be a linear operator on a finite dimensional vector space $V$. A nonzero vector $x\in V$ is a **generalized eigenvector** of $T$ if there exists a scalar $\lambda$ such that  $(T-\lambda I)^p (x) = 0$ for some $p\in \mathbb{Z}^+$. We call $x$ the corresponding **generalized eigenvector**.

* Let $T$ be a linear operator on a vector space $V$ and let $x$ be a generalized eigenvector of $T$ corresponding to the eigenvector $\lambda$. If $p$ denotes the smallest positive integer such that $(T-\lambda I)^p=0$, then the ordered set
  $$
  \set{(T-\lambda I)^{p-1}(x), \cdots, (T-\lambda I)(x), x}
  $$
  is called a **[[Cyclic Group|cycle]] of generalized eigenvectors** of $T$ corresponding to $\lambda$. $(T-\lambda I)^{p-1}$ is called the **initial vector** and $x$ the **end vector**. The **length** of such a cycle is $p$.
	* (*Friedberg e7.1.4*) Let $Z$ be a cycle of generalized eigenvectors of $T$ on $V$  corresponding to eigenvalue $\lambda$. Then $\text{span}(Z)$ is a $T$-invariant subspace of $V$. 
	* (*Friedberg e7.1.5*) Each cycle is uniquely determined by the eigenvectors. That is, if they are distinct, then two cycles $Z_i, Z_j$ are disjoint.

* (*Friedberg 7.1*) Let $T$ be a linear operator on $V$ and $\gamma$ be a cycle of generalized eigenvectors of $T$ corresponding to $\lambda$
	* The initial vector of $\gamma$ is an eigenvector of $T$ corresponding to the eigenvalue $\lambda$ and no other member of $\gamma$ is an eigenvector of $T$.
	* $\gamma$ is linearly independent.
	* Let $\beta$ be an ordered basis for $V$. Then $\beta$ is a Jordan Canonical Basis for $V$ if and only if $\beta$ is a disjoint union of cycles of generalized eigenvectors of $T$. 

* Let $\lambda$ be an eigenvalue of a linear operator $T$ on a vector space $V$. The **generalized eigenspace** of $T$ corresponding to $\lambda$ is defined as 
  $$
  K_\lambda =\set{x\in V \mid (T-\lambda I)^p (x) = 0, p\in \mathbb{Z}^+}
  $$
* (*Friedberg 7.2*) $K_\lambda$ is a $T$-[[Invariant Subspace|invariant subspace]] containing $E_\lambda$, the [[Eigenspaces and Eigenbases|eigenspace]] of $T$ corresponding to $\lambda$.
* (*Friedberg Lem.7.3*) Let $T$ be a linear operator on a vector space $V$ and let $\lambda_1,\dots,\lambda_k$ be distinct eigenvalues of $T$. Let $x_i\in K_{\lambda_k}$. If 
  $$
  x_1 + x_2 + \dots + x_k = 0
  $$
  Then $x_i=0$ for all $i$
* (*Friedberg 7.3*) Let $T$ be a linear operator on a finite dimensional vector space $V$ with distinct eigenvalues $\lambda_1,\dots, \lambda_k$. Let $S_i\subseteq K_{\lambda_i}$ be a linearly independent subset. Then 
  $$
  \forall i\ne j, S_i \cap S_j = 0
  $$
  And $S=S_1\cup\dots\cup S_k$ is a linearly independent subset of $V$.
* (*Friedberg 7.4*) Let $T$ be a linear operator on a finite dimensional vector space $V$ and $Z_I$ be a cycle of generalized eigenvectors of $T$ corresponding to the eigenvalue $\lambda$ and having initial vector $y$. If the $y_i$'s are distinct and the set $\set{y_1,\dots,y_q}$ is linearly independent, then the $Z_i$'s are disjoint and 
  $$
  Z =\bigcup_{i=1}^n Z_i
  $$
* (*Friedberg 7.5*) Let $T$ be a linear operator on an $n$-dimensional vector space $V$ such that the characteristic polynomial of $T$ splits. Then there exists a Jordan Canonical Basis for $T$ -- an ordered basis $\beta$ that is a disjoint union of generalized eigenvectors of $T$. 

* (*Friedberg 7.6*) Let $T$ be a linear operator on a finite dimensional vector space $V$ such that the characteristic polynomial of $T$ splits. Suppose $\lambda_1,\dots,\lambda_k$ are the distinct eigenvalues of $T$ with corresponding multiplicities $m_1,\dots, m_k$. Then
	* $\dim(K_{\lambda_I})=m_i$ 
	* If for each $i$, $S_i$ is a basis for $K_{\lambda_i}$, then the union $S=\cup_{i=1}^k S_k$ is a basis for $V$.
	* If $\beta$ is a Jordan Canonical basis for $T$, then for each $i$ $\beta_i=\beta\cap K_{\lambda_I}$ is a basis for $K_{\lambda_i}$.
	* $K_{\lambda_i}= N((T-\lambda_iI)^{m_i}$ 
	* $T$ is diagonalizable if and only if $E_{\lambda_i}=K_{\lambda_i}$ 

* (*Friedberg 7.7*) Let $T$ be a linear operator on a finite dimensional vector space $V$ for which the characteristic polynomial of $T$ splits. Then $V$ is a [[Vector Sum and Direct Sum|direct sum]] of the generalized eigenspaces of $T$.

* We can express the Jordan canonical basis $\beta$ as the following union
  $$
  \beta= \bigcup_{i=1}^k \beta_i
  $$
  Where each $\beta_i$ corresponds to the Jordan Canonical Basis for the restriction of $T$ to $K_{\lambda_i}$ where each $\lambda_i$ is a distinct eigenvalue of $T$ and the characteristic polynomial of $T$ splits.
	* *Notation*: If $\beta_i$ is a disjoint union of cycles $Z_1,\dots,Z_{k_i}$ with lengths $p_1,\dots,p_k$, we adopt the convention that the basis is ordered in decreasing order of cycle length so that $p_1 \ge p_2 \ge \dots \ge p_{k_i}$.   

* A **dot diagram** is a way of visualizing the form of matrix $A$ in Jordan canonical basis $\beta_i$.
	* The array consists of $k_i$ columns, one for each cycle.
	* From left to right the $j$-th column consists of $p_j$ dots corresponding to the members of $Z_j$. The lowermost dot of the column corresponds to $x_j$, the end vector of $Z_j$. 

* (*Friedberg 7.8*) For any positive integer $r$, the basis vectors in $\beta_i$ that are associated with the dots in the first $r$ rows of a dot diagram for $\beta_i$ form a basis for $N((T-\lambda_iI)^r)$. Hence the number of dots in the first $r$ rows of a dot diagram of $\beta_i$ equals $\text{nullity}((T-\lambda_iI)^r)$ 
* (*Friedberg 7.8.1*) Let $\beta_i$ be a Jordan canonical basis for the restriction of $T$ to $K_{\lambda_i}$ and suppose that $\beta_i$ is the disjoint union of $k_i$ cycles of generalized eigenvectors corresponding to $\lambda_i$. Then $\dim(E_{\lambda_i})=k_i$.
  
  Thus in the Jordan canonical form of $T$, For each eigenvalue $\lambda$, the number of Jordan blocks corresponding to $\lambda$ equals $\dim(E_\lambda)$. 

* (*Friedberg 7.9*) Let $r_j$ denote the number of dots in the $j$-th row of a dot diagram for $\beta_i$. Then
  $$
  r_j = \begin{cases}
  \dim(V) - \text{rank}(T-\lambda_i I) & \text{if } j = 1 \\
  \text{rank}((T-\lambda_iI)^{j-1}) & \text{if } j > 1
  \end{cases}
  $$
* (*Friedberg 7.9.1*) For any eigenvalue $\lambda_i$ of $T$, the dot diagram for $\beta_i$ is unique. Thus, subject to our convention for writing the Jordan Canonical Form -- the Jordan Canonical form of a linear operator is unique up to ordering of eigenvalues. 

* (*Friedberg 7.10*) Let $A$ and $B$ be two square matrices of the same size, each having Jordan Canonical forms in standard form. Then $A$ and $B$ are [[Vector Coordinate System|similar]] if and only if they have (up to permutation of eigenvalues) the same Jordan Canonical form. 
# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]