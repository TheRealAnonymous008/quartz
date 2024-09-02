* Let $A\in M_{m\times n}(F)$. The following operations on the rows or columns of $A$ are called **elementary row / column operators**
	* Interchanging any two rows / columns of $A$.
	* Multiplying any row / column of $A$ by a nonzero constant.
	* Adding any constant multiple of a row / column of $A$ to another row / column of $A$
* An **elementary matrix** is a matrix obtained by performing on $I_n$. 
	* Type 1: Interchange two rows / columns of $I_n$
	* Type 2: Multiply any row / column of $I_n$ by a nonzero constant.
	* Type 3: Adding any constant multiple of a row / column to another.

* (*Friedberg 3.1*) 
  Row variant:
  Let $M_{m\times n}(F)$ and suppose that $B$ is obtained from $A$ by performing an elementary row operation. Then there exists an $m\times m$ elementary matrix $E$ such that $B=EA$. In fact $E$ is obtained by performing the corresponding row operation on $I_m$. Conversely, if $E$ is an elementary $m\times m$ matrix, then $EA$ is a matrix that can be obtained by performing an elementary row operation on $A$.
  
  Column Variant:
  Let $M_{m\times n}(F)$ and suppose that $B$ is obtained from $A$ by performing an elementary column operation. Then there exists an $n\times n$ elementary matrix $E$ such that $B=AE$. In fact $E$ is obtained by performing the corresponding column operation on $I_n$. Conversely, if $E$ is an elementary $n\times n$ matrix, then $AE$ is a matrix that can be obtained by performing an elementary column operation on $A$.
  
* (*Friedberg 3.2*) Elementary matrices are [[Matrix Inversion|invertible]]. Their inverse is an elementary matrix of the same type.
* (*Friedberg 3.4.1*) Elementary row and column operations on a matrix are rank-preserving.
* (*Friedberg 3.6*) Let $A\in M_{m\times n}(F)$ such that $\text{rank}(A)=r$. Then $r\le m, r\le n$ and by means of a finite number of elementary row and column operators $A$ can be transformed into a matrix $D$ such that
  $$
  D_{ij} = \begin{cases}
  0 & i\ne j \\
  1 & i = j, i \le r \\
  0 & i = j, i  >r 
  \end{cases}
  $$
	* (*Friedberg 3.6.1*) Let $A\in M_{m\times n}(F)$ such that $\text{rank}(A)=r$. Then there exists invertible matrices $B\in M_{m\times m}(F)$ and $C\in M_{n\times n}(F)$ respectively such that $D=BAC$, where $D$ is the matrix in (*Friedberg 3.6*)
	* (*Friedberg 3.6.3*) An invertible matrix is a product of elementary matrices.

# Systems of Linear Equations
* A system of linear equations of the form
  $$
  \begin{cases}
  a_{11} x_1 + a_{12}x_2 +\dots + a_{1n} x_n = b_1 \\
  a_{21} x_1 + a_{22}x_2 +\dots +a_{2n} x_n = b_2 \\ 
  \vdots \\
  a_{m1}x_1 + a_{m2}x_2 + \dots + a_{mn} x_n = b_n
  \end{cases}
  $$
  Can be represented compactly using an $m\times n$ matrix
  $$
  A = 
  \begin{bmatrix}
  a_{11} & \dots & a_{1n} \\ 
  \vdots & \ddots & \vdots \\
  a_{m1} & \dots & a_{mn}
  \end{bmatrix}
  $$
  And vectors
  $$
  x = \begin{bmatrix}
  x_1 \\
  \vdots \\ 
  x_n
  \end{bmatrix},
  b = \begin{bmatrix}
  b_1 \\
  \vdots \\ 
  b_m
  \end{bmatrix}
  $$
  So that we are solving 
  $$
  Ax = b
  $$
  Or more specifically, finding $s\in F^n$ such that
  $$
  As=b
  $$
  We refer to the above as a **system of linear equations**


* A system $Ax=b$ of $m$ equations in $n$ unknowns is **homogeneous** if $b=0$ and **non-homogeneous** otherwise.
  
  Any homogeneous system has at least one solution, namely the trivial solution of all $0$'s.

* (*Friedberg 3.8*) Let $Ax=0$ be a homogeneous system of $m$ linear equations in $n$ unknowns over field  $F$. Let $K$ denote the set of all solutions to $Ax=0$. Then 
  $$
  K =N(L_A)
  $$
  And also $K\le F^n$  
  
  And
  $$
  \dim(K) = \dim(N(L_A)) = n-\text{rank}(L_A) = n-\text{rank}(A)
  $$
* (*Friedberg 3.8.1*) If $m<n$, then $Ax=0$ has a nontrivial solution.
* (*Friedberg 3.9*) Let $K$ be the solution set of a system of linear equations $Ax=b$, and $K_H$ be the solution set of the corresponding homogeneous system $Ax=0$. Then for any solution $s$
  $$
  K =\{s\} + K_H
  $$
  [^kernel]


[^kernel]: [[Vector Sum and Direct Sum]].  An analogy from Group Theory can be made: Define the homomorphism $\phi$ as the one associated with the linear transformation $L_A$. Then $K=\ker(\phi)$ and what we are saying is that any solution $s$ has an associated family of solutions (i.e., [[Cosets, Group Indices|entire cosets]]).

* (*Friedberg 3.10*) Let $Ax=b$ be a system of $n$ equations in $n$ unknownsn. If $A$ is invertible, then the system has exactly one solution -- $A^{-1}b$. 
  
  Conversely, if the system has exactly one solution then $A$ is invertible.

* (*Friedberg 3.11*) Let $Ax=b$ be a system of linear equations. Then the system has at least one solution if and only if 
  $$
  \text{rank} (A) = \text{rank} (A\mid B)
  $$
* (*Friedberg 3.12*) A system $Ax=b$ has a solution if and only if $b\in R(L_A)$

* Two systems of $m$ linear equations in $n$ unknowns are **equivalent** if they have the same solution set.

* (*Friedberg 3.13*) Let $(S):Ax=b$ be a system of $m$ linear equations in $n$ unknowns and let $C$ be any invertible $m\times m$ matrix. Then the system $(S'):(CA)x=Cb$ is equivalent to $s$.
* (*Friedberg 3.13.1*) If $(A'\mid B')$ is obtained from $(A\mid B)$ by a finite number of elementary row operations, then the system $A'x=b'$ is equivalent to the original system

* To solve a linear system of equations, we use the associated matrix $A$ and using elementary row operations, reduce it to **row echelon form**. That is:
	* Any row containing a nonzero entry precedes any row in which all the entries are zero (if any)
	* The first nonzero entry in each row is the only nonzero entry in its column.
	* The first nonzero entry in each row is $1$ and it occurs in a column to the right of the leading $1$ in any preceding column
* (*Friedberg 3.14*) We can transform a matrix to row echelon form using **Gaussian Elimination**
	* Transform the augmented matrix into an upper triangular matrix.
	* Using backwards substitution, transform the upper triangular matrix to row echelon form.
* *Gaussian Elimination transforms a matrix to row echelon form using the fewest arithmetic operations*

* (*Friedberg 3.15*) Let $Ax=b$ be a system of $m$ nonzero equations in $n$ unknowns. Suppose $\text{rank}(A)=\text{rank}(A\mid B)$ and $(A\mid B)$ is in row echelon form.
	* $\text{rank}(A)=m$
	* If the general solution is of the form 
	  $$
	  s=s_0 + t_1u_1 + t_-2u_2 + \dots + t_{n-m}u_{n-m}
	  $$
	  Then $\{u_1,\dots,u_{n-m}\}$ is [[Linear Combination|basis]] for the solution set of the corresponding homogeneous system and $s_0$ is a solution in the original system. 

* The method for solving systems of linear equations can be phrased as applying a [[Polynomial Ring|division algorithm process]] repeatedly to change a given [[Groebner Basis|ideal basis]] into one that better illustrates the geometry of the associated algebraic variety. 
 
# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]
* [[Matrix]]