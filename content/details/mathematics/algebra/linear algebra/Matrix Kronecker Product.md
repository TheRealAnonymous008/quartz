* The **Kronecker product** of two matrices $A\in M_{n\times m}(F)$ and $B\in M_{p\times q} (F)$ is defined as $A\otimes B \in M_{np\times mq}(F)$  where
  $$
  A\otimes  B = \begin{bmatrix}
  a_{11}B & \cdots & a_{1m} B \\
  \vdots & \ddots & \vdots \\
  a_{n1} B & \cdots & a_{nm}B 
  \end{bmatrix}
  $$

* The following identity holds
  $$
  (A\otimes B) (C\otimes D) = (AC) \otimes (BD)
  $$

* The **Kronecker Sum** of two [[Matrix|matrices]] $A\in M_{n\times n}(\mathbb{R})$ and $B\in  M_{m\times m}$ is defined as 
  $$
  A \oplus B = (A \otimes I_m) + (I_n \otimes B)
  $$
	* (*Mesbahi e3.17*) The following holds
	  $$
	  e^{A\oplus B} = e^A \otimes e^B
	  $$




  

# Links
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt]]