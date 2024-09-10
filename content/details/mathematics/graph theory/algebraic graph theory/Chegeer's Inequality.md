* Let $\varepsilon(S,S^C)$ be the number of edges needed to separate $S$ from its complement. That is
  $$
  \varepsilon(S,S^C) = \text{card} (\set{v_iv_j \in E \mid (v_i \in S, v_j \in S^C) \wedge (v_i\in S^C, v_j \in S)})
  $$
  We define the **edge conductance** to be the ratio of the [[Graph Connectivity|cut]] defined above with the smaller of $S$ and $S^C$. That is 
  $$
  \phi(S) = \frac{\varepsilon(S,S^C)}{\min(|S|, |S^C|)}
  $$
  The **graph conductance** (also called **isoperimetric number**) is defined as
  $$
  \phi(G) = \min_{S\subseteq V} \phi(S) 
  $$
	* *Intuition*: The isoperimetric number is a measure of the level of connectedness in the graph (and hence, how robust it is to edge deletion)


* **Cheeger's Inequality**  Let $G$ be an undirected graph and $\lambda_2$ be the second smallest eigenvalue of the [[Graph Laplacian|Laplacian]] matrix. Then
  $$
  \frac{\phi(G)^2 }{2\Delta(G)} \le \lambda_2(G) \le \phi(G) 
  $$

# Links
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt]]