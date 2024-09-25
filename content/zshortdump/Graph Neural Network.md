* Graph neural networks are [[Neural Network|neural network]] architectures specifically designed for learning representations of graph-structured data including learning node representation. 
  
  More formally the problem solved by GNNs can be framed as follows. Let $G=(V,E)$ be a graph and $A(G)$ be the [[Matrices in Graph Theory|Adjacency Matrix]]. We also let $X\in \mathbb{R}^{|V|\times C}$ be the **attribute matrix** on the $C$ node features. 
  
  The goal is to learn a node representation in $F$ dimensions, denoted $H\in \mathbb{R}^{|V|\times F}$ such that the graph structural information and node attributes are preserved.

# Supervised Learning



# Misc
* The following challenges are apparent in graph [[Representation Learning|representation learning]] and motivate advances in GNNs. 
	* High Computational [[Complexity Theory|complexity]] which limits its applicability to large networks.
	* Low [[Multiprogramming|Parallelizability]] since edges imply coupling between nodes.
	* [[Pathologies of Deep Learning|Non-stationarity]] - samples from graph data are dependent on each other. 

# Links
* [[Graph Neural Networks -- Foundations, Frontiers and Applications by Wu et al.]]

* [[Graph Theory]]