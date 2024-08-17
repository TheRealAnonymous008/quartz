* An $m\times n$ **matrix** with entries from a field $F$ is a rectangular array of the form
  $$
  \begin{bmatrix}
  a_{11} & a_{12} & \cdots & a_{1n} \\
  a_{21} & a_{22} & \cdots & a_{2n} \\
  \vdots & \vdots & \ddots & \vdots \\
  a_{m1} & a_{m2} & \cdots & a_{mn} 
  \end{bmatrix}
  $$
  Where all the entries are elements of $F$.

* A matrix is **square** if it has the same number of rows and columns
* Two matrices $A,B$ are equal if and only if $\forall 1\le i \le m, 1 \le j \le n, A_{ij} = B_{ij}$

* The set of $m\times n$ matrices is a [[Vector Space]] denoted $M_{m\times n }(F)$ under matrix (element-wise) addition and scalar multiplication.

* The **transpose** $M^T$ of an $m\times n$ matrix $M$ is the $n\times m$ matrix where $M^T_{ij} = M_{ji}$
	* $(AB)^T=B^TA^T$
  
  A matrix is **symmetric** if 
  $$
  M^T = M
  $$

	* The set of symmetric matrices is a subspace of $M_{n\times n}(F)$
	* The transpose can be seen in the context of [[Dual Space|dual spaces]]
* A matrix is **skew-symmetric** if 
  $$
  M^T = -M
  $$
	* (*Friedberg e1.3.26*) The set of skew-symmetric $n\times n$ matrices is a [[Vector Subspace|subspace]] of $M_{n\times n}(R)$. In fact, let $W_1$ be the set of skew-symmetric and $W_2$ the set of symmetric matrices. Then
	  
	  $$
	  M_{n\times n} (R) = W_1 \oplus W_2 
	  $$
	  *Every matrix is the sum of a symmetric and skew symmetric matrix*.


* A matrix is **diagonal** if $D_{ij}$ whenever $i\ne j$. 
	* The set of diagonal matrices is a subspace of $M_{n\times n}(F)$ 

* The **trace** of an $n\times n$ matrix, denoted $\text{tr}(M)$ is the sum of all entries of $M$ in the diagonal. That is
  
  $$
  \text{tr} (M) = M_{11} + M_{12} + \dots + M_{nn}
  $$
	* (*Friedberg e1.2.6*) The set of $n\times n$ matrices having trace equal to $0$ is a subspace of $M_{n\times n}(F)$ 

* Every matrix is [[Linear Transformation Matrix Isomorphism|equivalent to a linear transformation]]
# Topics
* [[Matrix Multiplication]]
* [[Matrix Inversion]]
# Links
* [[Linear Algebra by Friedberg Insel and Spence]]