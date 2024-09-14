* The **Cartesian Product** of [[Fundamental Constructs of Graph Theory|graphs]] $G_1=(V_1,E_1)$ and $G_2=(V_2, E_2)$ is defined as 
  $$
  G = G_1\square G_2
  $$
  such that $V(G) = V_1 \times V_2$ and vertices $(v_1,v_2)$ and $v_1', v_2')$ in $V(G)$ are adjacent if and only if  either the following hold
  (1) $v_1 = v_1'$ and $(v_2,v_2')$ is an edge in $E_2$
  (2) $v_2=v_2'$ and $(v_1,v_1')$ is an edge in $E_1$. 
	* The Cartesian Product is both commutative and associative.
	* The Cartesian Product preserves [[Graph Connectivity|connectedness]]. 

* A graph is **prime** if the identity $G=G_1\square G_2$ suggests that either $G_1$ or $G_2$ are trivial. 
* (*Mesbahi 3.24*) Every [[Graph Connectivity|connected graph]] can be written as a Cartesian Product of prime graphs. Such a decomposition is unique up to reordering of factors [^cartesian_decomp]

[^cartesian_decomp]: This is analogous to the [[Abelian Group|Fundamental Theorem of Finitely Generated Abelian Groups]]

# Links
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt|Mesbahi and Egerstedt]]