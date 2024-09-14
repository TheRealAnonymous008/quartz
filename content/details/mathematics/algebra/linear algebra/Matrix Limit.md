* Let $L, A_1, A_2, \dots\in M_{n\times p}(\mathbb{C})$ . The sequence $A_1,A_2,\dots$ is said to **converge**  to the matrix $L$ called the **limit** of the sequence if $\forall i,j$ 
  $$
  \lim_{m\to \infty}(A_m)_{ij} = L_{ij}
  $$
  We denote this by saying that
  $$
  \lim_{m\to\infty}A_m = L
  $$

* (*Frieidberg 5.17*) Let $A_1,A_2,\dots \in M_{n\times p}(\mathbb{C})$ such that
  $$
  \lim_{m\to\infty} A_m = L\in M_{n\times p}(\mathbb{C})
  $$
  Then for any $P\in M_{r\times n}(\mathbb{C})$ and $Q\in M_{p\times s}(\mathbb{C})$ we have that
  $$
  \begin{split}
  \lim_{m\to \infty} PA_m &= PL \\
  \lim_{m\to\infty} A_mQ &= LQ
  \end{split}
  $$
* (*Friedberg 5.17.1*) Let $A\in M_{n\times n}(\mathbb{C})$ and $\lim_{m\to\infty}A^m=L$. Then for any invertible matrix $Q\in M{n\times n}(\mathbb{C})$ we have
  $$
  \lim_{m\to \infty}(QAQ^{-1})^m = QLQ^{-1}
  $$ 
* Let $S=\{\lambda\in \mathbb{C} \mid |\lambda| < 1 \text{ or } \lambda = 1\}$. This set consists of the complex number $1$ and the interior of the disk of radius $1$ in the complex plane.
	* If $\lambda$ is a complex number, $\lim_{m\to\infty}\lambda^m$ exists if and only if $\lambda\in S$ 
	* (*Friedberg 5.18*) Let $A$ be a square matrix with complex entries. Then $\lim_{m\to\infty}A^m$ exists if and only if the following hold
		* If $\lambda$ is an [[Matrix Diagonalization|eigenvalue]] of $A$, then $\lambda \in S$
		* If $1$ is an eigenvalue of $A$ then the dimension of the [[Eigenspaces and Eigenbases|eigenspace]] corresponding to $1$ equals the algebraic multiplicity of $1$ as an eigenvalue of $A$.
	* (*Friedberg 5.19*) Let $A\in M_{n\times n}(\mathbb C)$ be such that the following hold
	  If $\lambda$ is an eigenvalue of $A$, then $\lambda \in S$ 
	  $A$ is diagonalizable. 
	  
	  Then  $\lim_{m\to\infty}A^m$ exists.
		* This gives us a technique for computing matrix limits on diagonalizable matrices -- first express the matrix as $QDQ^{-1}$ then compute the limit as shown in (*Friedberg 5.17*) 

* Let $A\in M_{n\times n}(\mathbb{C})$. $p_i(A)$ is the sum of the absolute values of the entries of row $i$. $v_j(A)$ is the sum of the absolute values of the entries of column $j$
  $$
  \begin{split}
  p_i(A) &= \sum_{j=1}^n |A_{ij}| \\
  v_j(A) &= \sum_{i=1}^n |A_{ij}| 
  \end{split}
  $$
  The **row sum** $p(A)$ and the **column sum** $v(A)$ are defined as
  $$
  \begin{split}
  p(A) &= \max \set{p_i(A) \mid 1\le i \le n} \\
  v(A) &= \max \set{v_j(A) \mid 1\le j \le n}
  \end{split}
  $$

* (*Friedberg 5.21, Mesbahi 3.9*) **Gerschgorin's Disk Theorem**. Let $A\in M_{n\times n}(\mathbb{C})$ define
  $$
  r_i = p_i(A) - |A_{ii}|
  $$
  and let $C_i$ denote the disk centered at $A_{ii}$ of radius $r_i$. Then each eigenvalue of $A$ lies in some $C_i$.  More formally, each eigenvalue is located in 
  $$
  \bigcup_{i}\bigg\{z\in \mathbb{C} \mid |z -A_{ii}| \le \sum_{j\ne i } |A_{ij}|\bigg\}
  $$
	* (*Friedberg 5.21.1*) Let $\lambda$ be any eigenvalue of $A$. Then 
	  $$
	  |\lambda| \le p(A)
	  $$
	* (*Friedberg 5.21.2*) Let $\lambda$ be any eigenvalue of $A$. Then 
	  $$
	  \lambda \le \min(p(A), v(A))
	  $$
* (*Friedberg 5.23*) Let $A\in M_{n\times n}(\mathbb{C})$ be a matrix in which each entry is positive and let $\lambda$ be an eigenvalue of $A$ such that $|\lambda|=p(A)$ . Then $\lambda = p(A)$ and $\{u\}$ is a basis for $E_\lambda$ where
  $$
  u = \begin{bmatrix}
  1 \\
  \vdots \\ 
  1
  \end{bmatrix}
  $$
	* (*Friedberg 5.23.1*) Let $A\in M_{n\times n}(C)$ be a matrix in which each entry is positive and let $\lambda$ be an eigenvalue of $A$ such that $|\lambda|=v(A)$. Then $\lambda=v(A)$ and $\dim (E_\lambda)= 1$ 

* If $A\in M_{n\times n}(\mathbb{C})$, we define $e^A$ as 
  $$
  \begin{split}
  e^A &= \lim_{m\to \infty} B_m \\
  B_m &= I + A + \frac{A^2}{2!} + \dots + \frac{A^m}{m!}
  \end{split}
  $$
  Thus, $e^A$ is the sum of the infinite series
  $$
  e^A = I + A + \frac{A^2}{2!} + \cdots
  $$
	* (*Friedberg e5.3.19*) Let $D = P^{-1}AP$ be a diagonal matrix. Then
	  $$
	  e^A = Pe^D P^{-1}
	  $$

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt|Mesbahi and Egerstedt]]

* [[Real Analysis]]
* [[Matrix]]