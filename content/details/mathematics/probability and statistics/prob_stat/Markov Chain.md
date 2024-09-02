* A [[Probability Theory|stochastic process]] is said to be **Markovian** or has the **Markov Property** if the next state is only dependent on the previous state. That is, if we let $X_t$ be the state at time $t$ then 
  $$
  P(X_{t+1} \mid X_t,\dots, X_0) = P(X_{t+1} \mid X_t)
  $$
* A Markov process is *memoryless*. It does not remember the history of past states beyond the current state. 

* A Markov Chain can be expressed using a **transition [[Matrix]]** $M$.  In this case $(M^m)_{ij}$ represents the probability of moving from state $j$ to state $i$ in $m$ steps. 
  
  Each distribution on states can be represented with a **probability vector**
	* A transition matrix is called **regular** if it only contains positive entries. 

* (*Friedberg 5.20*) Let $M\in M_{n\times n}(\mathbb{R})$ such that it has nonnegative entries; $x\in \mathbb{R}^n$ having nonnegative coordinates and $u\in \mathbb{R}^n$ be the column vector in which each coordinate equals $1$. Then
	* $M$ is a transition matrix if and only if $M^Tu=u$
	* $x$ is a probability vector if and only if $u^Tx=(1)$ 
	* (*Friedberg 5.20.1a*) The product of two $n\times n$ transition matrices is an $n\times n$ transition matrix. In particular, any power of a transition matrix is a transition matrix.
	* (*Friedberg 5.20.1b*) The product of a transition matrix and a probability vector is a probability vector.

* (*Friedberg 5.21.3*) If $\lambda$ is an [[Matrix Diagonalization|eigenvalue]] of a transition matrix, then $|\lambda|\le 1$
	* Follows from [[Matrix Limit|Gerschgorin's Disk Theorem]]
* (*Friedberg 5.22*) Every transition matrix has $1$ as an eigenvalue.
* (*Friedberg 5.23.2*) Let $A\in M_{n\times n}(\mathbb{C})$ be a transition matrix in which each entry is positive and let $\lambda$ denote any eigenvalue of $A$ other than $1$. Then $|\lambda| < 1$. Moreover, the dimension of the eigenspace corresponding to the eigenvalue $1$ is $1$. 

* (*Friedberg 5.24*) Let $A$ be a regular transition matrix
	* If $\lambda$ is an eigenvalue of $A$ then $|\lambda|\le 1$
	* If $|\lambda|=1$, then $\lambda =1$ and $\dim(E_\lambda)=1$. 
	* (*Friedberg 5.24.1*) Let $A$ be a regular transition matrix that is diagonalizable. Then $\lim_{m\to \infty}A^m$. 
* (*Friedberg 5.25*) Let $A$ be an $n\times n$ regular transition matrix. Then 
	* The multiplicity of $1$ as an eigenvalue of $A$ is $1$
	* $\lim_{m\to \infty}A^m$ exists
	* $L=\lim_{m\to\infty} A^m$ is a transition matrix
	* $AL=LA=L$
	* The columns of $L$ are identical. Each column of $L$ is equal to the unique probability vector $v$ that is also an eigenvector corresponding to eigenvalue $1$ of $A$.
	* For any probability vector $x$
	  $$
	  \lim_{m\to\infty} (A^m x) = v
	  $$
	  We call $v$ the **fixed probability vector**. Also called the **stationary vector** of the regular transition matrix $A$. 


# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]
