 * **Preferential Attachment** pertains to a phenomenon where new nodes prefer to link to more connected nodes. 
	  $$
	  \Pi(k_i)=\frac{k_i}{\sum_j k_j}
	  $$
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

# Degrees of Preferential Attachment 
* Preferential Attachment exists in various degrees. It exists based on  the coefficient $\alpha$
	* **Sublinear** $\alpha < 1$ occurs in random networks 
	* **Linear** $\alpha = 1$ which occurs in scale-free networks. This acts as a phase transition 
	* **Superlinear** $\alpha  > 1$ which shows up for hub and spoke networks. 
![[Degrees of Preferential Attachment.png]]


# Models of Preferential Attachment 
* Many models that can show networks with preferential attachment is that *preferential attachment appears to be a byproduct of large, complex networks regardless if we use randomness or rational choice to  grow the network.*

## Copying Model
* The **Copying Model** is a local mechanism that generates a scale-free network without explicitly using preferential attachment. 

* To decide where a new node connects, randomly select a node $u$ corresponding to a "related" node. Then, follow a two-step procedure:
	* With probability $p$, the new node links to $u$
	* With probability $1-p$ choose an outgoing link of $u$ and link the new node to the link's target. That is, connect to a neighbor of the target, not the target itself. 

* Preferential attachment is seen in this network. 
  Let  $N$ be the number of nodes in the network.
  
  The probability of choosing any node is $\frac{1}{N}$
  The probability of selecting a degree $k$ node via the second step is $\frac{k}{2L}$.
  
  Then, the probability that a new node connects to a degree $k$ node is given as
  $$
  \Pi (k) = \frac{p}{N} + \frac{1-p}{2L}k
  $$
  Which has linear preferential attachment. This indicates that the network generated is indeed scale-free.

## Link Generation Model 
* The **Link Generation Model** *generates [[Scale Free Networks]] without explicitly using preferential attachment *.
	* At each time step, [[Operations on Graphs#Vertex Operations|add]] a new node to the network. 
	* Select a link at random and connect the new node to one of the two nodes at the two ends of the selected link. 

* Even without explicit mention of preferential attachment, this model is still capable of generating preferential attachment.
* *Linear preferential attachment is apparent*.


## [[Scale Free Networks#Barabasi-Albert Model|Barabasi-Albert Model]] 

## Optimization Model
* The **Optimization Model** is a global mechanism which aims to explain the topology of networks based on [[Characterizing the Decision Problem|rational choice]]. 
* Suppose we have a cost function 
  $$
  C_i=\min_j(\delta d_{ij} + h_j)
  $$
  Where 
  $d_{ij}$ denotes the cost of an edge
  $h_j$ denotes  the distance of the node from the first node of the network.

* Three phenomena can arise 
	* If $\delta < (1/2)^{1/2}$ a hub and spoke network arises since connecting to the central node is prioritized 
	* If $\delta \ge N^{\frac{1}{2}}$,, then the cost term dominates and each node connects greedily to minimize locale extrema, resulting in a [[Random Networks|random graph]]. 
	* If $4 \ge \delta \ge N^{\frac{1}{2}}$, the generated network is scale-free because 
		* We correlate an optimum to connecting with the central node. This center becomes a hub but also any node close to the center becomes a hub by virtue of connecting new nodes towards it.
		* Because we are optimizing, nodes tend towards the optima (i.e., the hubs). Thus, there is preferential attachment
		  
	  ![[Optimization Model.png]]
# Links 
* [[Network Science by Barabasi]]
* [[Fundamental Constructs of Network Science]]