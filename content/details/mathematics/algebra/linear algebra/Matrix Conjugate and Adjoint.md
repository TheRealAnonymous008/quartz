* Let $A\in M_{m\times n}(F)$. The **conjugate transpose** (also called **adjoint**) of $A$ is $A^\ast\in M_{n\times m}(F)$ defined such that
  $$
  (A^\ast)_{ij}=\overline{A_{ji}}
  $$
	* (*Friedberg e6.2.10*) Let $A\in M_{n\times n}(\mathbb{C})$  such that the rows of $A$ form an [[Orthogonality and Orthonormality|orthonormal]] set. Then
	  $$
	  AA^\ast = I
	  $$
* The [[Linear Transformation Matrix Isomorphism|equivalent concept in the language transformations]] is the **linear adjoint**
* (*Friedberg 6.8*) Let $V$ be a finite dimensional [[Inner Product Space|inner product space]] over $F$ and let $g:V\to F$ be a [[Linear Transformation|linear transformation]]. Then, there exists a unique vector $y\in V$ such that $g(x)=\braket{x,y}$ $\forall x\in V$. 
	* *Intuition*: Let $\beta$ be an orthonormal basis $\set{x_1,\dots,x_n}$. The vector
	  $$
	  y= \sum_{i=1}^n \overline{g(x_i)} x_i
	  $$
* (*Friedberg 6.9*) Let $V$ be a finite dimensional inner product space and let $T$ be a linear operator on $V$. Then there exists a unique linear function $T^\ast:V\to V$ such that $\forall x,y\in V$ such that
  $$
  \braket{T(x), y} = \braket{x,T^\ast (y)}
  $$
  This linear function $T^\ast$ is called the **adjoint** of $T$.

* (*Friedberg 6.10*) Let $V$ be a finite-dimensional inner product space and let $\beta$ be an orthonormal basis for $V$. If $T$ is a linear operator on $V$ then
  $$
  [T^\ast]_\beta = [T]_\beta^\ast 
  $$

* (*Theorem 6.11*) Let $V$ be a finite-dimensional inner product space, and let $T$ and $U$ be linear operator on $V$. Then
	* $(T+U)^\ast = T^\ast + U^\ast$
	* $(cT)^\ast = \overline{c}T^\ast$ for any $c\in F$.
	* $(TU)^\ast = U^\ast T^\ast$
	* $T^{\ast\ast}=T$
	* $I^\ast = I$
	* (*Friedberg e6.3.8*) If $T$ is invertible then so is $T^\ast$ and in fact
	  $$
	  (T^\ast)^{-1} = (T^{-1})^\ast
	  $$
* (*Theorem 6.11.1*) Results analogous to (*Theorem 6.11*) can be stated for matrices. Let $A,B\in M_{n\times n}(F)$
	* $(A+B)^\ast = A^\ast + B^\ast$
	* $(cA)^\ast = \overline{c}A^\ast$ for any $c\in F$.
	* $(AB)^\ast = B^\ast A^\ast$
	* $A^{\ast\ast}=A$
	* $I^\ast = I$
	* If $A$ is invertible, then so is $A^\ast$ and in fact
	  $$
	  (A^\ast)^{-1} = (A^{-1})^\ast
	  $$
	* (*Friedberg e6.3.16*) If $A\in M_{n\times n}(F)$ then the [[Determinant|determinant]] satisfies
	  $$
	  \det(A^\ast) = \overline{\det(A)}
	  $$
* (*Friedberg Lem6.12.2*) Let $A\in M_{m\times n}(F)$. Then
  $$
  \text{rank}(A^\ast A) = \text{rank}(A)
  $$
* (*Friedberg Cor6.12.1*) If $A\in M_{m\times n}(F)$ such that $\text{rank}(A)=n$. Then $A^\ast A$ is [[Matrix Inversion|invertible]]

* (*Friedberg 6.12*) Let $A\in M_{m\times n}(F)$ and $y\in F^m$. Then there exists $x_0\in F^n$ such that $(A^\ast A)x_0 = A^\ast y$ and $\forall x\in F^n$
  $$
  ||Ax_0-y|| \le ||Ax - y|| 
  $$
  Furthermore if $\text{rank}(A)=n$ and 
  $$
  x_0 = (A^\ast A)^{-1} A^\ast y
  $$

* (*Friedberg e6.3.13*) Let $T$ be a linear operator on a finite dimensional inner product space $V$. The following [[Dimension Theorem|statements]] are true 
	* $N(T^\ast T)=N(T)$
	* $\text{rank}(T^\ast T)=\text{rank}(TT^\ast) = \text{rank}(T)$
	* $\text{rank}(T)=\text{rank}(T^\ast)$ 
	* For any $A \in M_{n\times n}(F)$, 
	  $$
	  \text{rank}(A^\ast A) = \text{rank}(AA^\ast) = \text{rank}(A)
	  $$
# Topics
* [[Normal Matrix]]
* [[Self-Adjoint Matrix]]


# Links
* [[Linear Algebra by Friedberg Insel and Spence]]