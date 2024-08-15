* If $S_1,S_2$ are nonempty subsets of $V$. The **sum** of $S_1$ and $S_2$ is the set
  
  $$
  S_1 + S_2 = \{x+y \mid x\in S_1, y\in S_2 \}
  $$
* A vector space $V$ is said to be the **[[Direct Product of Groups|direct sum]]** of $W_1$ and $W_2$, denoted $V=W_1\oplus W_2$ if $W_1,W_2\le V$ such that $W_1\cap W_2 = \{0\}$ and $W_1 + W_2 = V$
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

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]