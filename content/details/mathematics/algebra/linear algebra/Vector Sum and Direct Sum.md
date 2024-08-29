* If $S_1,S_2$ are nonempty subsets of $V$. The **sum** of $S_1$ and $S_2$ is the set
  
  $$
  S_1 + S_2 = \{x+y \mid x\in S_1, y\in S_2 \}
  $$
  In general for $S_1,\dots S_k \subseteq V$, we define the sum as
  $$
  \sum_{i=1}^kS_i = S_1 + \dots +S_k = \set{x_1+\dots + x_k : x_i \in S_i, 1\le i \le k}
  $$
* A vector space $V$ is said to be the **[[Direct Product of Groups|direct sum]]** of $W_1$ and $W_2$, denoted $V=W_1\oplus W_2$ if $W_1,W_2\le V$ such that $W_1\cap W_2 = \{0\}$ and $W_1 + W_2 = V$
  
  In general for subspaces $W_1,\dots, W_k\le V$  we have that $V$ is the direct sum , denoted $V=\bigoplus_{i=1}^k W_i = W_1\oplus \dots \oplus W_k$  if 
  $$
  V=\sum_{i=1}^k W_i
  $$
  And $\forall i$
  $$
  W_i \cap \left(\sum_{j\ne i} W_j \right) = \{0\}
  $$

  
* (*Friedberg e1.6..20*) If $W_1, W_2$ are finite dimensional [[Vector Subspace|subspaces]] such that $V=W_1+W_2$. Then $V$ is also finite dimensional and
  $$
  \text{dim}(W_1+W_2) = \dim(W_1) + \dim(W_2) - \dim(W_1\cap W_2)
  $$
  Moreover, $V=W_1\oplus W_2$ if and only if
  $$
  \dim(V) = \dim(W_1) + \dim(W_2)
  $$
* (*Friedberg e1.6.24*) If $W_1\le V$ where $V$ is finite-dimensional, then there is a subspace $W_2\le V$ such that $V=W_1\oplus W_2$ 
	* *Intuition*: A [[Linear Combination|basis]] of $W_1$ is linearly independent in $V$. Such a set can be extended to a basis in $V$. The vectors we add to such a basis defines the subspace $W_2$.

* (*Friedberg 5.15*) Let $W_1,\dots, W_k \le  V$ where $V$ is a finite dimensional vector space. The following are equivalent
	* $V=\bigoplus_{i=1}^k W_i$ 
	* $V=\sum_{i=1}^k W_i$ and for any vectors $x_1,\dots, x_k$ where $x_i\in W_i$ 
	  $$
	  x_1+\dots + x_k = 0 \implies \forall i \ \  x_i =0
	  $$
	* Each vector $v\in V$ can be uniquely written as $v=x_1+x_2 + \dots + x_k$ , $x_i\in W_i$.
	* If for each $i: 1\le i \le k$, $\gamma_i$ is an ordered basis for $W_i$ then 
	  $$
	  \gamma_1\cup \dots \cup \gamma_k
	  $$
	  is an ordered basis for $V$. The order comes by first listing all of $\gamma_1$, then $\gamma_2$ and so on.
	* For each $i: 1\le i \le k$., there exists an ordered basis $\gamma_i$ for $W_i$ such that $\gamma_1\cup\dots\cup \gamma_k$ is an ordered basis for $V$.
	* (*Friedberg e5.2.18*) 
	  $$
	  \dim(V) = \sum_{i=1}^k \dim(W_i)
	  $$

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]