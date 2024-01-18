* The **link probability** is the probability that a link exists between two nodes. 
* The **Degree Distribution** is a [[Random Variables and Probability Distributions|probability distribution]] that provides the probability that a randomly selected node in the graph has degree $k$. This is denoted $p_k$
	* It can be obtained using [[Frequentist Statistics]]. Let $N_k$ denote the number of nodes in the network with degree $k$, and $N$ the total nodes. Then
	  $$
	  p_k=\frac{N_k}{N}
	  $$
	* A **hub** is a node in the network whose number of links greatly exceeds the average degree 

* The **degree exponent** of a power law is the exponent found in the power law.  More specifically if 
  $$
  p_k = Ck^{-\gamma}
  $$
  then $\gamma$ is the degree exponent 


# Preferential Attachment 
* **Preferential Attachment** pertains to a phenomenon where new nodes prefer to link to more connected nodes. 
	  $$
	  \Pi(k_i)=\frac{k_i}{\sum_j k_j}
	  $$

* Preferential Attachment exists in various degrees. It exists based on  the coefficient $\alpha$
	* **Sublinear** $\alpha < 1$ occurs in random networks 
	* **Linear** $\alpha = 1$ which occurs in scale-free networks. This acts as a phase transition 
	* **Superlinear** $\alpha  > 1$ which shows up for hub and spoke networks. 
![[Degrees of Preferential Attachment.png]]

* Preferential Attachment can be measured. The relative change of degree over time follows 
  $$
  \frac{\Delta k_i}{\Delta t} \sim \Pi (k_i)
  $$

* The **empirical preferential attachment** is measured based on the real network.
	* We can measure the preferential attachment when we know the time in which each node joined the network, or we have two snapshots of the network collected at not too distant moments in time.
	* Say we have two snapshots, the first at $t$ and the second at $t+\Delta t$.  For nodes that have changed degree during the time frame, measure $\Delta k_i = k_i(t+\Delta t) - k_i (t)$, which is the relative change of the degree of node $i$. 
	* We can approximate $\Pi(k)$ with $k^\alpha$. 

* The **Cumulative Preferential Attachment Function** is a function that shows the sum of empirical preferential attachments of each node added before node $k$.
  
  $$
  \pi (k) = \sum_{k_i = 0}^k \Pi(k_i)
  $$

# Percolation 
* In a percolation process the **average cluster size** is defined as $$\braket{s}=|p-p_c|^{-\gamma_p}$$Where
	  $p_c$ is the breakdown threshold 
	  $\gamma_p$ is the critical exponent.
	  As $p\to p_c$ this value diverges 


* The **clustering coefficient** is a quantity, denoted $C_v$ which captures the degree to which the neighbors of $v$ link to each other to form a clique. 
  Let 
  $v$ be a vertex, with degree $d$.
  $L$ be the number of edges between the $d$ neighbors of $v$. 
  
  The clustering coefficient is calculated as 
  $$
  C_v=\frac{2L}{d(d-1)}
  $$
  It should be noted that 
  $$
  0\le C_v\le 1
  $$
  

* A **phase transition** for property $A$ occurs at a point $x$ such that given a threshold function and a network property $n$ -- 
	* If $n<x$ then the property does not hold. We call this region a *subcritical region*
	* If $n > x$, then the property does hold. We call this region a *supercritical region*.

# Classes of Networks 
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
# Links
* [[Network Science by Barabasi|Barabasi]]
* [[Fundamental Constructs in Graph Theory]]
* [[Graph Connectivity]]
* [[Random Variables and Probability Distributions]]
