* A [[Relation]] $\delta:M_{n\times n}(F)\to F$ is said to be an **$n$-linear function** (a.k.a. **multilinear function**) if $\delta$ is a linear function of each row of an $n\times n$ [[Matrix]] when the remaining $n-1$ rows are held fixed. That is 
  $$
  \delta
  \begin{pmatrix}
  A^{(1)} \\
  \vdots \\
  cA^{(i)} + A^{(i)'} \\
  \vdots\\
  A^{(n)}
  \end{pmatrix}
  = 
  c \cdot
  \begin{pmatrix}
  A^{(1)} \\
  \vdots \\
  cA^{(i)} \\
  \vdots\\
  A^{(n)}
  \end{pmatrix} +
  \delta
  \begin{pmatrix}
  A^{(1)} \\
  \vdots \\
  A^{(i)'} \\
  \vdots\\
  A^{(n)}
  \end{pmatrix}
  $$
  Whenever 
  $$
  \begin{pmatrix}
  A^{(1)} \\
  \vdots \\
  cA^{(i)} + A^{(i)'} \\
  \vdots\\
  A^{(n)}
  \end{pmatrix}\in M_{n\times n}(F)
  $$

* (*Friedberg 4.3*) Any [[Linear Combination]] $n$ linear functions is an $n$ linear function 

* An $n$-linear function $\delta$ is **alternating** if $\delta (A) = 0$ whenever two adjacent rows are identical.

* Let $\delta:M_{n\times n}(F)$ be an alternating $n$-linear function. Then the following are true.
	* If $B$ is obtained by [[Elementary Matrix Operations|interchanging any two rows]] of $A\in M_{n\times n}$ then 
	  $$
	  \delta(B)=-\delta(A)
	  $$
	* If two rows of an $n\times n$ matrix $A$ are identical, then $\delta(A)=0$

* (*Friedberg 4.5*) Let $\delta$ be an alternating $n$-linear function on $M_{n\times n}(F)$. For each $(n+1)\times (n+1)$ matrix $A$ and each $j$, $1\le j \le n+1$ define 
  $$
  \epsilon_j(A) = \sum_{i=1}^{n+1} (-1)^{i+j}A_{ij}\cdot \delta(\tilde{A}_{ij})
  $$
  Where $\tilde{A_{ij}}$ is the $n\times n$ matrix obtained from $A$ by deleting the $i$-th row and $j$-th column.
  
  Then $\epsilon_j$ is an alternating $(n+1)$-linear function on the $(n+1)\times(n+1)$ matrices with entries from $F$.

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]