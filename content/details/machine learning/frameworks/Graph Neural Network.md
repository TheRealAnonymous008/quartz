* Graph neural networks are [[Neural Network|neural network]] architectures specifically designed for learning representations of graph-structured data including learning node representation. 
  
  More formally the problem solved by GNNs can be framed as follows. Let $G=(V,E)$ be a graph and $A(G)$ be the [[Matrices in Graph Theory|Adjacency Matrix]]. We also let $X\in \mathbb{R}^{|V|\times C}$ be the **attribute matrix** on the $C$ node features. 
  
  The goal is to learn a node representation in $F$ dimensions, denoted $H\in \mathbb{R}^{|V|\times F}$ such that the graph structural information and node attributes are preserved.
* Each layer in a GNN has two different functions
	* *Aggregate* information from the neighbors of each node.
	* *Combine* aggregated information from neighbors with current node representations.

* The general framework can be described as follows. Let $H^t_v$ be the representation of vertex $v$ at time step $t$.
  
  We have that
  $$
  \begin{split}
  H^0 &:= X & \ \ \ \ \forall v\in V \\ 
  a_v^t &: = \text{aggregate}\set{H_u^{t-1} \mid u\in N(v)}  \\
  H_b^t &:= \text{combine }\set{H_v^{t-1}, a_v^t}
  \end{split}
  $$
  Note the similarity to [[Recurrent Neural Network|LSTMs and GRUs]]. 
  
  To use the representations, we use the representations at the last layer. That is $H^T$. 

# Issues
* The following challenges are apparent in graph [[Representation Learning|representation learning]] and motivate advances in GNNs. 
	* High Computational [[Complexity Theory|complexity]] which limits its applicability to large networks.
	* Low [[Multiprogramming|Parallelizability]] since edges imply coupling between nodes.
	* [[Pathologies of Deep Learning|Non-stationarity]] - samples from graph data are dependent on each other. 

* Another problem is the **Over-smoothing Problem** That is, if the network is too deep *representations become too similar*
* One approach to alleviate it is using the **PairNorm**. The goal is to *keep the total pairwise squared distance of node representations unchanged*. 
	* In particular, we want 
	  $$
	  \text{TPSD}(\hat{H}) = \text{TPSD}(X)
	  $$
	  Or
	  $$
	  \sum_{ij\in E(G)} ||\hat{H}_i-\hat{H}_j||^2 + \sum_{ij\notin E(G)} ||\hat{H}_i - \hat{H}_j|| ^2  = \sum_{ij\in E(G)} ||\hat{X}_i-\hat{X}_j||^2 + \sum_{ij\notin E(G)} ||\hat{X}_i - \hat{X}_j|| ^2
	  $$
	* The above computation can be simplified by noticing that
	  $$
	  \text{TPSD}(\hat{H}) = \sum_{(i,j)\in V} ||\hat{H}_i - \hat{H}_j|| ^2 = 2|V|^2 \left(\frac{1}{N}\sum_{i=1}^{|V|} ||\hat{H}_i||^2_2 -\left|\left|\frac 1 {|V|} \sum_{i=1}^{|V|}  \hat{H}_i \right|\right|^2_2 \right)
	  $$
	  Where $||\cdot||_2$ is the L2-[[Inner Product Space|Norm]].
	  
	  Which can be further simplified using 
	  $$
	  \hat{H}_i^c = \hat{H}_i - \frac{1}{|V|}\sum_{i=1}^{|V|} \hat{H}_i
	  $$
	  So that
	  $$
	  \text{TPSD}(\hat{H}) = \text{TPSD} (\hat{H}^c) = 2N||\hat{H}^c || ^2_F
	  $$
	  And we want too update $\hat{H}_i$ using the rule
	  $$
	  \hat{H}_i = s\sqrt{|V|} \cdot \frac{\hat{H_i^c}}{\sqrt{||\hat{H}^c||^2_F}}
	  $$

# Topics
* [[Supervised Graph Neural Network]]
* [[Unsupervised Graph Neural Network]]


# Links
* [[Graph Neural Networks -- Foundations, Frontiers and Applications by Wu et al.]]

* [[Graph Theory]]