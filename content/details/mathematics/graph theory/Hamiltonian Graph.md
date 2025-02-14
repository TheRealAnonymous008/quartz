* A **Hamiltonian Path** is a [[Trails, Walks, Paths and Cycles|path]] contained within a [[Fundamental Constructs of Graph Theory|graph]] such that it passes through vertex exactly once.
* A **Hamiltonian Cycle** is a cycle contained within a Graph such that it passes through each vertex exactly once.
* A **Hamiltonian Graph** is a graph which contains a Hamiltonian Cycle
* A graph is **Semi-Hamiltonian** if it contains a Hamiltonian Path but not a Hamiltonian Cycle

* (*Bondy and Murty 4.2*) If $G$ is Hamiltonian, then for every non-empty $S\subset V$. 
  $$
  \omega(G-S) \le |S|
  $$
* (*Bondy and Murty 4.3*) **Dirac's Theorem**. If $G$ is a graph with $n\ge 3$ vertices and $\delta \ge \frac{n}{2}$ then $G$ is Hamiltonian.

* *(Wilson 7.1)* **Ore's Theorem** [^2]. Let $G$ be a simple graph with $n\ge 3$ vertices. If $$\deg(v)+\deg(w)\ge n$$for each pair of non-adjacent vertices $v$ and $w$, then $G$ is Hamiltonian

[^2]: Ore's Theorem generalizes Dirac's Theorem




* (*Godsil 3.6.1*) Let $X$ be a cubic graph, then $L(S(X))$ has a Hamiltonian cycle if and only if $X$ does.

# Links
* [[Introduction To Graph Theory by Wilson]]
* [[Graph Theory With Applications by Bondy and Murty]]
* [[Algebraic Graph Theory by Godsil and Royle|Godsil and Royle]]