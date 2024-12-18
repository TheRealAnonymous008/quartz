* The **agreement set** $A\subseteq \mathbb{R}^n$ is defined as
  $$
  A = \text{span} \set{1} = \set{x\in \mathbb{R}^n \mid x_i = x_j \ \ \forall i, j}
  $$
  That is *it is the set of fixed points in the dynamics -- the set where all units "agree" on their states*

* The [[Differential Equation|rate of change]] of each unit's state is assumed to be governed by the sum of its relative states with respect to a subset of other neighboring units. That is if $i$ is a unit with neighborhood $N(i)$, then 
  $$
  \dot x_i(t) = \sum_{j\in N(i)} (x_j(t) - x_i (t))
  $$
  The **agreement dynamics** can also be represented using the [[Graph Laplacian|Laplacian]] of the information network $G$ and assuming $x(t)\in \mathbb{R}$
  $$
  \dot{x}(t) = -L(G) x(t)
  $$
	* If $x\in \mathbb{R}^n$, $n> 1$, then we can represent the above as 
	  $$
	  \dot x(t) = - L(G) \otimes x(t) 
	  $$
## Static Agreement over Undirected Graphs
* Consider the eigendecomposition of $L(G)=U\Lambda U^T$. We have
  $$
  x(t) = e^{-L(G) t }x(0)
  $$
  Which can be [[Eigenspaces and Eigenbases|decomposed]] along each eigen-axis as follows
  $$
  x(t) =\sum_{i=1}^n e^{-\lambda_1t} u_i^T x_0u_i
  $$
* (*Mesbahi 3.4*) Let $G$ be a connected graph. Then the undirected agreement protocol converges to an agreement set with a rate of convergence proportional to $\lambda_2 (G)$. 
* We define the **centroid** as 
  $$
  1^T x(t) = \sum_{i} x_i(t)
  $$
  *The centroid is a constant of motion for the agreement dynamics*
* The state trajectory generated by the agreement protocol converges to the [[Projection|projection]] of its initial state onto the agreement subspace. That is
  $$
  \lim_{t\to\infty} x(t) \to (u_1^Tx_0 u_i)= \frac{1^T x_0}{n} 1 
  $$

* (*Mesbahi 3.5*) A necessary and sufficient condition for the agreement protocol to converge to the agreement subspace from an arbitrary initial condition is that the underlying graph contains a [[Spanning Trees and Forests|spanning tree]]. 
	* *Intuition*: Convergence is governed by $\lambda_2(G)>0$ which implies that the graph is [[Graph Connectivity|connected]], that there is a spanning tree
	* *Consensus is possible as long as a graph is connected*
## Static Agreement over Directed Graphs
* (*Mesbahi 3.12*) For a [[Directed Graph|digraph]] $D$ containing an arborescence, the state trajectory satisfies
  $$
  \lim_{t\to \infty} x(t) = (p_1q_1^T) x_0 
  $$
  Where $p_1$ and $q_1$ are the right and left eigenvectors associated with the zero eigenvalue of $L(D)$ normalized such that $p_1q_1 = 1$. 
  
  Thus $x(t)\to A$  for all initial conditions if and only if $D$ contains an arborescence.
* (*Mesbahi 3.13*) Let $q$ be the left eigenvector of the digraph in-degree Laplacian associated with its zero eigenvalue. Then $q^Tx(t)$ is invariant under the agreement dynamics.

* (*Mesbahi 3.17*) *The agreement protocol over a digraph reaches the average consensus for every initial condition if and only if it is weakly connected and balanced.*

* The progress of the agreement dynamics can be monitored using discrete time intervals using a [[Markov Chain|markov process]] defined by
  $$
  \begin{split}
  z(k+1) &= e^{-\delta L(D)}z (k) \\
  z(k) &= x(\delta k)
  \end{split}
  $$
	* (*Mesbahi 3.18*) For all digraphs $D$ and sampling intervals $\delta$ we have
	  $$
	  \begin{split}
	  e^{-\delta L(D)}1 &= 1 \\
	  e^{-\delta L(D)} & \ge 0 
	  \end{split}
	  $$
	  Thus $e^{-\delta L(D)}$ is a stochastic matrix whose  right and left eigenvectors are those of $L(D)$ associated with $e^{\delta\lambda_i}$ 
	* (*Mesbahi 3.19*) The state of the nodes during the evolution of the agreement protocol over a digraph $D$ at any time instance is a convex combination of the values of all nodes at the previous instance. 
	* (*Mesbahi 3.21*) The behavior of the agreement dynamics is characterized by its action on the unit simplex.

* (*Mesbahi 3.26*) **Factorization Lemma for Agreement Dynamics**. 
  
  Let $G_1,\dots, G_n$ be a finite set of graphs. Let $x_1(t),\dots, x_n(t)$ be the states of the agreement protocols initialized from $x_1(0),\dots, x_n(0)$.
  
  $$
  \dot{x}_i = -L(G_i) x_i (t)
   $$
   Then the state trajectory generated by the agreement protocol of the [[Cartesian Product of Graphs|Cartesian Product]]
   $$
   \dot x(t) = L(G_1 \square \cdots\square G_n) x(t) 
   $$
   is
   $$
   x(t) = x_1(t) \otimes \dots \otimes x_n(t)
   $$
   Initialized from
   $$
   x(0) = x_1(0)\otimes \dots\otimes x_n(0)
   $$
	* *Intuition*: The proof follows from direct computation. 

* (*Mesbahi 3.27*) The agreement dynamics over a composite graph can always be represented as a [[Matrix Kronecker Product|Kronecker product]] of agreement dynamics over its prime factors. Such a factorization is unique up to reordering.  
# Links
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt]]