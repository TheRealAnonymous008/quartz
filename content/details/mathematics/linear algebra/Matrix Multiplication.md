* The **product** of $A\in M_{m\times n}(F)$ and $B\in M_{n\times p}(F)$ is the $m\times p$ matrix such that
  $$
  (AB)_{ij} = \sum_{k=1}^nA_{ik}B_{kj}
  $$

* (*Friedberg 2.12*) For any $n\times n$ matrix $A$ 
  $$
  I_nA = AI_n = A
  $$
* (*Friedberg 2.13*) Let $A\in M_{m\times n}(F)$ and $B,C\in M_{n\times p}(F)$ and $a\in F$
	* $A(B+C)=AB+AC$
	* $a(AB)=(aA)B=A(aB)$
	* $$
	  A\left(\sum_{i=1}^k a_iB_i\right) = \sum_{i=1}^k a_iAB_i
	  $$
	* (*Friedberg 2.14*) 
		* $(AB)_j = AB_j$
		* $B_j = Be_j$

* (*Friedberg 2.17*) *Matrix multiplication is associative* 
  $$
  A(BC) = (AB)C
  $$
* (*Friedberg e2.3.12*) 
  $$
  \begin{split}
  \text{tr}(AB)&=\text{tr}(BA) \\
  \text{tr}(A) &= \text{tr}(A^T)
  \end{split}
  $$

* **Batch Matrix Multiplication** is an operation $\text{BMM}$ that extends matrix multiplication to allow it to be performed per batch.
  
  More formally, if we have inputs
  $$
  \begin{equation} \begin{split}
  A &= [A_1, \dots, A_n] \in \mathbb{R}^{n\times a \times b} \\
  B &= [B_1, \dots, B_n] \in \mathbb{R}^{n\times b \times c} \\
  \end{split}\end{equation}
  $$
  Then 
  $$
  \text{BMM}(A,B)=[A_1 B_1, \dots, A_n B_n] \in \mathbb{R}^{n\times a \times c}
  $$

# Links
* [[Matrix]]
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]