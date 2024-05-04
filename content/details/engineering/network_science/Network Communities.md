* A **community** is a group of nodes within a network that have a higher likelihood of connecting to each other than to nodes from other communities. 
* The **Community Hypotheses** are fundamental to network communities
	* *Fundamental Hypothesis* - A network's community structure is uniquely encoded in its [[Fundamental Constructs of Graph Theory|Wiring diagram]]
	* *Connectedness and Density Hypothesis* - a community is a locally dense, [[Graph Connectivity|connected]] subgraph of the network
	* *Random Hypothesis* - [[Random Network|random networks]] lack an inherent community structure
	* *Maximal modularity Hypothesis*  - for a given network, the partition with maximum modularity corresponds to the optimal community structure
		* The **modularity** measures the quality of a community partition in a network. 
		  
		  More formally, let 
		  
		  $N$ be the number of nodes
		  $L$ be the number of links 
		  $n_c$ be the number of community, 
		  $A_{ij}$ denote the adjacency matrix of the network. 
		  $p_{ij}$ denote the expected number of links between nodes $i$ and $j$ if the network was randomly wired. 
		  
		  For a community $c$, let 
		  
		  $N_c$ be the number of nodes
		  $L_c$ be the number of links
		  $k_c$ be the total degree of the community
		  
		  The **modularity** of a community is denoted $M_c$ and defined as 
		  $$
		  M_c=\frac{1}{2L} \sum_{(i,j)\in C_c} (A_{ij} - p_{ij}) = \frac{L_c}{L} - \left(\frac{k_c}{2L}\right)^2
		  $$
		  It is the difference between the partition of the network and the randomly wired network.
		  
		  The **modularity** of the whole network is simply the sum of the modularities of the communities.
		  $$
		  \begin{equation} 
		  \begin{split}
		  M&=\sum_{c=1}^{n_c} M_c  \\ 
		  &= \sum_{c=1}^{n_c} \left[ \frac{L_c}{L}-\left(\frac{k_c}{2L}\right)^2 \right]
		  \end{split}\end{equation}
		  $$
		* Higher Modularity implies a better community structure.
		* Zero Modularity implies the community structure is no better than a[[Random Network]].
		* Negative Modularity implies no community structure between the nodes.

* The **internal degree** of node $i$ in a network is the number of links that connect $i$ o other nodes in its community $C$. It is denoted $k_i^\text{int}(C)$.
* The **external degree** of node $i$ in a network is the number of links that connect $i$ to other nodes outside of its community $C$. It is denoted $k_i^\text{ext}(C)$

* A **strong community** is one where $\forall i \in C$
  $$
  k_i^\text{int}(C) > k_i^\text{ext} (C
  $$
* A **weak community** is one where $\forall i\in C$
  
  $$
    k_i^\text{ext}(C) > k_i^\text{int} (C
  $$

# Community Detection Algorithms
* **Community Detection** is a problem in the context of networks. Given some network $N$, we wish to find its community structure -- the number of communities and their sizes. 
	* The **community size distribution** which captures the sizes of the communities in the network is, according to empirical studies, an *intrinsic property of the network*.

* Community detection via a brute-force approach is computationally expensive (to be exact, it scales with the Bell Numbers $B_N$, so it has exponential time complexity).
  
  Thus, we want algorithms that can uncover the underlying community structure of a network.

## Hierarchical
### Ravasz Algorithm
* The **Ravasz Algorithm** is an agglomerative [[Clustering]] algorithm for use in community detection
* It consists of the following steps
	* *Define the distance matrix between node pairs. *
	  
	  This captures the fact that nodes rom the same community tend to be similar. We do this using the Topological Overlap Matrix (see [[Fundamental Constructs of Graph Theory|here]])
	* *Measure the similarity of communities* using unweighted average linkage clustering
	* *Perform agglomerative clustering.* Merge communities with the highest similarity, and then repeat step 2. 
	  
	  Because clustering is agglomerative, we start with all nodes being their own communities, and we progressively merge communities together. 

* The The time complexity of each of the above steps are $O(N^2) + O(N^2) + O(N\log N)$Which means the time complexity is 
  $$
  O(N^2 )
  $$

### Girvan-Newman Algorithm 
* The **Girvan-Newman Algorithm** is a divisive clustering algorithm.
* It consists of the following steps
	* Define the distance matrix between node pairs. The distance between node pairs is determined by centrality. For computational performance, we use link betweenness centrality.
	  
	  *Higher centrality means nodes are more likely to belong to different communities. *
	* Initialize by having all nodes in one community. 
	  
	  *Remove the link with the largest centrality*. In case of a tie, choose one link randomly.
	  
	  Then, recalculate the centralities of all links for all clusters. Repeat until all links are deleted.

* The time complexity of the algorithm is determined by the calculation of the centrality.
  
  Using link betweenness, this centrality is $O(LN)$ (where $L$ and $N$ are the number of links and nodes respectively).

### Limitations
* It assumes a hierarchy exists in the network.
* By the density hypothesis, networks can be partitioned into communities that are weakly connected to other communities. However, this goes against the fact that [[Characterizing Real Networks and Network Phenomena|real networks are scale free]]
* It only gives a family of community structures rather than one that is correct, contradicting the fundamental hypothesis.
* These issues are resolved using the [[Models for Scale Free Networks#Hierarchical Network Model]]


## Modularity-Based
### Greedy Modularity Maximization Algorithm
* The following greedy algorithm aims to maximize the modularity of a given network
* It works as follows
	* Assign each node to its own community
	* Inspect each community pair connected by at least one link, and compute the modularity difference (denoted $\Delta M$) obtained if we merge them. 
	  
	  Merge the communities with the largest $\Delta M$. 
	* Repeat the above until all nodes merge into a single community.  
	  Record modularity $M$ for each timestep
	* Select the partition for which $M$ is maximal.
	  
* Each calculation for each $\Delta M$ can be done in constant time.
  
  We require $O(L)$ computations in step 2. 
  
  Updating the communities after merging requires $O(N)$. 
  
  The complexity is 
  $$
  O((L+N)N)
  $$


### Louvain Algorithm
* The **Louvain Algorithm** is a proposed alternative to the greedy modularity maximization algorithm that aims to have better scalability
* The procedure is as follows:
	* Start with a Weighted network of $N$ nodes and assign nodes to different communities
	  
	  Evaluate the gain in modularity if we place node $i$ in the community of one of its neighbors $j$.
	  
	  Move $i$ to the community of $j$ when the modularity gain is the highest, but only if the gain is positive.
	  
	  The gain is calculated as follows 
	  
	     Let
	   $C$ be a community 
	   $\sum_{in}$ be the sum of the weights inside $C$ 
	   $\sum_{tot}$ be the sum of the link weights of all nodes in $C$. 
	   $k_i$ is the total weight of the links incident to $i$ 
	   $k_{i \ ; \ in}$ be the sum of the weights of the links from $i$ to nodes in $C$
	   $W$ be the total weight of the network. 
	   $$
	   \Delta M= \left[\frac{\sum_{in}+2k_{i \ ; \ in}}{2W} - \left(\frac{\sum_{tot} + k_i}{2W}\right)^2\right] - \left[\frac{\sum_{in}}{2W} - \left( \frac{\sum_{tot}}{2W}\right)^2 - \left(\frac{k}{2W}\right)^2\right]
	   $$
	   
	  
	  
	  Do this for all nodes until no further improvement can be achieved
	
	* Construct a new network whose nodes are the communities identified in step $1$. The weights of the links between nodes is the sum of the weight of the links between nodes in the corresponding communities. Links between nodes of the same community lead to weighted self loops. 

	* Repeat step 1. Iterate until there are no more changes and maximum modularity is attained.

* The computations scale linearly with $L$. In subsequent passes, the number of nodes and links decreases. It is thus at worst $O(n\log n)$ 
* *Storage is the limiting factor of the algorithm.*

### Limitations
* There is a **resolution limit** wherein there is a threshold where modularity-based approaches fail to capture communities smaller than this threshold. This is because *modularity maximization forces smaller communities into larger communities
* The change in modularity brought by merging two communities $A$ and $B$ is given by  
  $$
  \Delta M_{AB} = \frac{L_{AB}}{L} - \frac{k_A k_B}{2L^2}
  $$
  
  Where 
  $L_{AB}$ denotes the number of links that connect the nodes in community $A$ with community $B$
  $k_A$ be the total degree of $A$
  $k_b$ be the total degree of $B$. 
  
	* If $A$ and $B$ are distinct communities, they should remain distinct when $M$ is maximized. However, this is not always the case.
	* f $2L \ k_Ak_B < 1$ , then $\Delta M_{AB} > 0$ if there is at least one link between the two communities, so $A and $B$ must be merged. 
	* If $k_A \sim k_B = k$, then 
	  $$
	  k\le \sqrt{2L}
	  $$
	  And the modularity increases by merging $A$ and $B$ into a single community, even if they are otherwise distinct. 
	  
	  This arises when $k_A, k_B$ are below the resolution limit. 
	* *Because real networks contain many small communities, modularity is not well suited for these*. 
	  


## CFinder
* The **Clique Percolation Algorithm** interprets communities as the union of overlapping cliques.
* We define the following terms
	* Two $k$-cliques are considered **adjacent** if they share $k-1$ nodes. (figure $b$)
	* A $k$-clique community is the largest component obtained as the union of all adjacent $k$ cliques.(figure $c$)
	* $k$-cliques that cannot be reached from a particular $k$-clique belong to other $k$-clique communities (figure $d$)

![[Clique Percolation.png]]

* The algorithm identifies all cliques and builds an $N_\text{clique}\times N_\text{clique}$ overlap matrix $O$ whose entries $O_{ij}$ denote the number of nodes shared by cliques $i$ and $j$ identified by a [[Percolation Theory|percolation process]] of adding nodes to existing communities,  provided it has sufficient overlap with the current clique being identified. 
* *It allows for nodes to belong to more than one community*.

* Finding cliques in the network grows exponentially (i.e., $O(e^N)$). 
* To interpret the overlapping community structure of a network, we must compare it to the community structure obtained for the degree randomized version of the network.

* A large $k$-clique community emerges in a [[Random Network]] only if the connection probability exceeds the threshold 
  
  $$
  p_c(k)=\frac{1}{[(k-1)N]^{1/(k-1)}}
  $$
  
  Thus, we expect only a few isolated $k$-cliques. Once $p>p_c(k)$, where $p$ is the link probability, we expect cliques that form $k$-clique communities.
	* *Thus, $k$-clique communities naturally emerge in sufficiently dense networks*



## Link Clustering
* The **link clustering algorithm** by Ahn, Bagrow, and Lehmann captures the fact that *while nodes can belong to multiple communities, links tend to be more community specific*. The links define the precise relationship between community members.
* It identifies links with a similar topological role in a network and then explores the connectivity patterns of the nodes. 

* It is performed as follows.
	* Identify the link similarity between links to obtain a link similarity matrix.
	* Apply hierarchical clustering  on the matrix using single linkage clustering.

* Performance wise, it is quadratic.
	* The calculation of similarity for nodes $i$ and $j$ depend on the degrees $k_i, k_j$, and requires $\max(k_i,k_j)$ steps. For typical networks, this remains as roughly quadratic time $O(N^2)$.
	* Clustering itself requires $O(L^2)$ steps 
	* In total, the algorithm requires $O(N^2) + O(L^2)$. That said, the $O(N^2)$ is technically a loose upper bound, and can be brought down when considering the degree exponent.  For [[Scale Free Network|scale free networks]], it is $O(N^{\frac{2}{\gamma-1}})$.

## Infomap
* **Infomap** is an algorithm that performs community detection, by *minimizing the [[Information Theory|length]] of the string needed to represent the network topology as viewed from a random walk* 
* Consider a network partitioned into $n_c$ communities. We wish to encode in the most efficient fashion the trajectory of a random walker on this network. This is based on the observation that the random network will tend to get trapped into communities.
  
  We do this by the following procedure:
	* Assign one code to each community via Huffman coding. This code is encoded in the **index codebook**
	* Assign codewords for each node within each community. This codeword can be reused in different communities
	  
	  We then optimize by minimizing
	  $$
	  L=qH(Q)+\sum_{c=1}^{n_c} p_{\odot}^c H(P_c) 
	  $$
	  Where 
	  $H(Q)$ is entropy
	  $q$ is the probability that the random walker switches communities.
	  
		* The first term of the formula corresponds to the average number of bits to represent the movement between communities.
		* The second term corresponds to the average number of bits to represent the movement within communities. $H(P_c)$ is the entropy of within-community movements.

* The goal is to minimize $L$ over all possible partitions. We can use [[#Louvain Algorithm|Louvain]] for this except we minimize $L$ instead of modularity.

* The computational performance is on par with the Louvain Algorithm. It is $O(N\log N)$ or $O(L\log L)$.
# Benchmarks
* We can compare the predicted communities of the algorithm to those planted in the benchmark as follows.
	* Consider an arbitrary partition into non-overlapping communities. At each step, randomly sample a node and record the label of the community it belongs to. This gives the probability distribution $p(C)$ on whether or not a node belongs to $C$.
* Consider two partitions of the same network, one being the benchmark (ground truth), and the other partition predicted by the algorithm. Each partition has its own $p(C_1)$ and $p(C_2)$ distribution. Consider the joint distribution $p(C_1, C_2)$ and *calculate the normalized mutual information $I_N$.*
	*  If $I_N$ is high, then the detected partitions are identical. Which means, the community detection algorithm can correctly identify community structure.

* When the link density within communities is high compared to their surroundings, most algorithms accurately identify the planted communities
* *The accuracy is benchmark dependent. *

## Girvan-Newmann Benchmark 
* The **Girvan-Newmann benchmark** generates a random graph where all nodes have comparable degree and all communities have identical size.
* The usual benchmark consists of $N=128$ nodes partitioned into $n_c=4$  communities. Each node is connected with probability $p^\text{int}$ to the nodes in its communities and $p^\text{ext}$ to nodes in the other three communities.
* The control parameter $$\mu = \frac{k^{ext}}{k^{ext}+k^{int}}$$captures the density differences within and between communities.
	* For small $\mu$, the algorithm performs well when nodes are more likely to cluster than connect to other communities.
	* For large $\mu$, the algorithm drops in performance since the community structure is more blurred as its density becomes comparable to the link density of the rest of the network.

* The main limitation with this benchmark is that it generates fat-tailed networks, which may not be in line with that observed i nreal networks.

![[GN Benchmark.png]]

## Lancichinetti-Fortunato-Radicchi Benchmark 
* The **Lancichinetti-Fortunato-Radicchi benchmark** generates a random network for which *degree distribution and community size distribution follow power laws. *

* The procedure is as follows
	* Start with $N$ nodes. Assign each to a community of size $N_c$, where $P_{N_C}\sim N_C^{-\zeta}$
	* Assign each node a degree $k_i$ sampled from a power law distribution where $p_k\sim k^{-\gamma}$.
	* Each node $i$ of a community receives an internal degree $(1-\mu)k_i$ and external degree $\mu k_i$. 
	* The stubs of nodes of the same community are randomly attached to each other until no more stubs are free. Thus we maintain the sequence of internal degrees of each node in its communities. The remaining stubs are attached to nodes from other communities.


![[LFR Benchmark.png]]

# Evolving Communities
* The following are empirical findings observed in social networks

* *Growth*: The probability that a node joins a community grows with the number of links that the node has to members of that community
* *Contraction*: Nodes with only a few links to members of their community are more likely to leave the community than nodes with multiple links to community members. 
	* In weighted networks the probability that a node leaves a community increases with the sum of its link weights to nodes outside the community.
* *Death* : The probability that a community disintegrates increases with the aggregate link weights to nodes outside the community.
* *Age*: Older communities tend to be larger.
* *Scalability*: The membership of large communities changes faster with time than the membership of smaller communities.

# Links
* [[Network Science by Barabasi|Barabasi]]
* [[Fundamental Constructs of Network Science]]