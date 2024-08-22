* A **determinant** on $M_{n\times n}(F)$ is an alternating [[Multilinear Function|multilinear function]] $\delta: M_{n\times n} (F) \to F$ such that $\delta(I_n)=1$. We denote this as $\det(A)$ or $|A|$.
  
  We can get an explicit, [[Recurrence Relations|recursive]] formula for the determinant below.

* (*Friedberg 4.5.1*)  Let $\delta$ be an alternating $n$-linear function on $M_{n\times n}(F)$. For each $(n+1)\times (n+1)$ matrix $A$ and each $j$, $1\le j \le n+1$ we can define the determinant as  
  $$
  \det(A) = \sum_{i=1}^{n+1} (-1)^{i+j}A_{ij}\cdot \det(\tilde{A}_{ij})
  $$
  Where $\tilde{A_{ij}}$ is the $n\times n$ matrix obtained from $A$ by deleting the $i$-th row and $j$-th column.

* (*Friedberg 4.5.2*) There exists a determinant on $M_{n\times n}(F)$ for any positive integer $n$. 

* (*Friedberg 4.6*) Any determinant $\det$ on $M_{n\times n}(F)$ has the following properties
	* If $B$ is a matrix obtained from $A$ by multiplying each entry of some row of $A$ by a scalar $c$, then
	  $$
	  \det (B) = c\cdot \det(A)
	  $$
		* (*Friedberg e4.3.6*) If $A\in M_{n\times n}(F)$ then
		  $$
		  \det(cA)=c^n\det(A)
		  $$
	* If two rows of $A$ are identical, then 
	  $$
	  \det(A) = 0
	  $$
	* If $B$ is a matrix obtained from $A$ by [[Elementary Matrix Operations|interchanging]] two rows, then
	  $$
	  \det(B) = -\det(A)
	  $$

	* If one row of $A$ consists entirely of zero entries, then
	  $$
	  \det(A) =0
	  $$
	* If $B$ is a matrix obtained from $A$ by adding a multiple of row $i$ to row $j$, $i\ne j$, then 
	  $$
	  \det(B) = \det(A)
	  $$
* (*Friedberg 4.6.1*) Let $E_1,E_n, E_3$ be elementary matrices in $M$ of types $1, 2, 3$ respectively. If $E_2$ is obtained by multiplying a row of $I$ by nonzero scalar $c$ then  for any determinant $\det$ 
	* $\det(E_1)=-1$
	* $\det(E_2)=c$
	* $\det(E_3)= 1$

* (*Friedberg 4.7*) Let $\det$ be a determinant on $M_{n\times n}(F)$ and let $A\in M_{n\times n}(F)$ such that $\text{rank}(A)<n$. (i.e., the matrix is not [[Matrix Inversion|invertible]]). Then
  $$
  \det (A) = 0
  $$


* (*Friedberg Lem.4.8*) If $E$ is an $n\times n$ elementary matrix with entries from $F$ and $\det$ is a determinant on $M_{n\times n}(F)$, then
  $$
  \det(AB) = \det(A) \cdot \det(B)
  $$
  For any $B\in M_{n\times n}(F)$

* (*Friedberg 4.8*) Let $\det$ be a determinant on $M_{n\times n}(F)$ and let $A,B\in M_{n\times n}(F)$. Then
  $$
  \det(AB)=\det(A)\cdot \det(B)
  $$

* (*Friedberg 4.8.1*) Let $A\in M_{n\times n}(F)$ be invertible. Then 
  $$
  \begin{split}
  \det (A) &\ne 0 \\
  \det(A^{-1}) &= \frac 1{\det(A)}
  \end{split}
  $$
* (*Friedberg 4.8.2*) Let $A\in M_{n\times n}(F)$. The following are equivalent
	* $\det(A)=0$
	* $A$ is not invertible
	* $\text{rank}(A) < n$ 

* (*Friedberg 4.9*) There is exactly one determinant on $M_{n\times n}(F)$

* (*Friedberg 4.10*) For any $A\in M_{n\times n}(F)$
  $$
  \det(A^T)=\det(A)
  $$
* (*Friedberg 4.10.1*) *Any statement about determinants involving rows can be restated in terms of the columns and vice versa*. 

* (*Friedberg 4.11*) The determinant of an upper triangular square matrix is the product of its diagonal entries.
* (*Friedberg 4.11.1*) If $A\in M_{n\times n}(F)$ is a lower triangular matrix, then the determinant of the matrix is the product of its diagonal entries.
* (*Friedberg e4.3.8*) If $B\in M_{n\times n}(F)$ is skew symmetric and $n$ is odd, then $\det(B)=0$


* (*Friedberg 4.12*) **Cramer's Rule** Let $Ax=b$ be the matrix form of a [[Elementary Matrix Operations#Systems of Linear Equations|system of linear equations]] with $n$ equations and $m$ unknowns. Let $x=(x_1,\dots, x_n)^T$ and $b=(b_1,\dots,b_n)^T$. If $\det(A)\ne 0$ then this system has a unique solution.
  
  Also $\forall k : 1\le k\le n$ then
  $$
  x_k = \frac{\det(M_k)}{\det(A)}
  $$
  Where $M_k$ is the $n\times n$ matrix obtained from $A$ by replacing the $k$-th column $A_k$ with $b$.


* A system of linear equations with integral coefficients has an integral solution if $\det(A)=\pm 1$. 

* (*Friedberg e4.3.9*) Let $A\in M_{n\times n}(F)$ be a matrix written in the form
  $$
  A = \begin{bmatrix}
  B_1 & B_2 \\
  O & B_3
  \end{bmatrix}
  $$
  Where $B_1,B_3$ are square matrices. Then
  $$
  \det(A) =\det(B_1) \cdot \det(B_3)
  $$ 
* (*Friedberg e4.3.15*) If $A\sim B$ then 
  $$
  \det(A) = \det(B)
  $$

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]
* [[Dimension Theorem]]