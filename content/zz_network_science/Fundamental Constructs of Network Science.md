# Important Quantities 
* The **degree $k$ probability** denoted $q_k$ is given as follows 
  
  $$
  q_k = Ckp_k
  $$
	* $C$ is a normalizing constant. Usually, this may be given as the average degree
	  $$
	  C=\frac{1}{\braket{k}}
	  $$
	* $p_k$ is the probability that any node has degree $k$. 

* The **link probability** is the probability that a link exists between two nodes. 
* The **Degree Distribution** is a [[Random Variables and Probability Distributions|probability distribution]] that provides the probability that a randomly selected node in the graph has degree $k$. This is denoted $p_k$
	* It can be obtained using [[Frequentist Statistics]]. Let $N_k$ denote the number of nodes in the network with degree $k$, and $N$ the total nodes. Then
	  $$
	  p_k=\frac{N_k}{N}
	  $$
	* A **hub** is a node in the network whose number of links greatly exceeds the average degree 
	* The **natural cutoff** of a degree distribution is the maximum degree, denoted $k_\text{max}$. *This arises from the finite nature of most graphs*.

* The **degree exponent** of a power law is the exponent found in the power law.  More specifically if 
  $$
  p_k = Ck^{-\gamma}
  $$
  then $\gamma$ is the degree exponent 


* The **link similarity** involving vertices $i,j,k$ of a graph $G$ is calculated as  
  
  $$
  S(ij,jk)=\frac{|\phi(i) \cap \phi(j)|}{|\phi(i)\cup\phi(j)|}
  $$
  Where $\phi(i)$ denotes the neighborhood of $i$ including itself.
	* The formula is really a variation of the Jaccard Index.
	* A high link similarity indicates that a link tends to connect to the same group of nodes. 
# Characteristics of Networks
* A **network property** is any property of a network. Usually it is something that can be described with a monotonic sequence
	* If some subgraph has the property, then any network that contains this subgraph has this property. 
	* Property $A$ *does not hold* if 
	  
	  $$
	  \lim_{N\to\infty}P(A)= 0
	  $$
	* Property $A$ *holds* if 
	  $$
	  \lim_{N\to \infty} P(A)=1
	  $$

* A network is **exponentially bounded** if its degree distribution decreases exponentially or faster for higher degrees. 
	* As a consequence we have that 
	  $$
	  \braket{k^2}<{\braket{k}}
	  $$
	* Here, the degrees of the network do not have variations 
	* *Examples*: Erdos-Renyi model; Watt-Strogatz model. 

* A  network is **fat tailed** if it has a fat tail in the region corresponding to high degree nodes 
	* As a consequence, we have that 
	  $$
	  \braket{k^2}>{\braket{k}}
	  $$
	* We expect outliers or exceptionally high-degree nodes in the network.
	* Most networks that fall under this classification are scale-free
# Classes of Network Models
* A **static network model** is a model for a network where the number of nodes is fixed, and we simply place the links between the nodes.
	* *The degree distribution of a static network model is bounded*.

* The **Evolving Network Model** is a model that captures the time evolution (i.e., growth) of a network. 

* A **generative network model** is a model where we generate a network with a predefined degree distribution. 
	* These models help us understand the relationship between various properties of the network with its degree distribution
	*  The **configuration model** allows us to generate a random network with pre-defined degree sequence by performing rewritings in the network.
	  
	  $$
	  p_{ij}=\frac{k_ik_j}{2L-1}
	  $$
		  * The obtained network will contain loops and multi-edges. 
		  * This model is desirable if we have a simple degree distribution
	* The **hidden parameter model** is an algorithm that generates a random network with predefined degree sequence but without loops or multi edges 
		* Start with $N$ isolated nodes and assign each hidden parameter $\eta_i\sim p(\eta)$. This hidden parameter can be sampled using either of the following 
			* From a predefined distribution 
			  $$
			  p_k=\int \frac{e^{-\eta} \eta ^k }{k!} p(\eta)d\eta 
			  $$
			* From a deterministic sequence 
			  $$
			  p_k=\frac{1}{N}\sum_j \frac{e^{-\eta_j} \eta_j ^k }{k!}
			  $$
		* This model is desirable if we do not know the average degree and want to generate a degree distribution with this average degree 
		* A [[Scale Free Networks|scale free network]] can be generated using the sequence 
		  $$
		  \begin{split}
		  \eta_j &= \frac{c}{i^\alpha} \\
		  p_k &\propto k^{-(1+\frac{1}{\alpha})}
		  \end{split}
		  $$

# Links
* [[Network Science by Barabasi|Barabasi]]

* [[Fundamental Constructs of Graph Theory]] - most constructs here are also relevant for network theory. 
* [[Graph Connectivity]]
* [[Random Variables and Probability Distributions]]
