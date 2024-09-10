* The breakdown of a complex [[Fundamental Constructs of Network Science|network]] is not gradual. Removing a small number of nodes only has a limited impact on integrity, but once a fraction of removed nodes reaches a critical threshold, the network abruptly breaks into disconnected components. 
	* *Random node failures induce a phase transition* from a [[Graph Connectivity|connected]] to disconnected network. 
	* [[Percolation Theory]] is applicable mostly for random and regular networks 

# Random Networks 
* Let $f$ be the fraction of nodes that were removed in an inverse percolation process. 
  
  For sufficiently large $f$, we break the [[Random Network#Theorem on Giant Components|giant component]] in the network. In this sense, we can use an inverse percolation process to understand the robustness of a network.
  
* As it turns out, the fragmentation of the network is not gradual, but characterized by a  threshold function determined by coefficient $f_c$.
  
  If $f<f_c$, then the giant component persists. However, once $f>f_c$, the giant component vanishes. 
  
  This is illustrated by the dependence on $f$ of the order parameter 
  
  In fact, we can analyze $f$ using the same  critical exponents  for the order parameter, correlation length and average cluster size This can be done by setting $f=1-p$.

# Scale Free Networks 
* Following an inverse percolation process during a breakdown, scale-free networks tend to have their largest component decrease in size gradually, vanishing in the vicinity of $f=1$ 
* This implies that scale-free networks have an unusual robustness to random node failures, which is different from the collapse of random networks (see [[#Random Networks|above]]).
* Intuitively, *the robustness of a [[Scale Free Network]] against random attacks comes from the fact that many nodes are of small-degree, and these do not impact the overall connectivity of the network.*

* By the Molloy-Reed Criterion of Scale Free Networks, the critical threshold only depends on the average degree and the second moment of the degree distribution.
* This helps us understand the source of the robustness of scale-free networks.
	* If the degree exponent  $\gamma < 3$, we have that the second moment $\braket{k^2}$ diverges as $N\to \infty$. 
	  
	  Inserting this yields that 
	  $$
	  \lim_{N\to\infty}f_c=1
	  $$
	  Which is what is observed empirically. 

	* We can extend $f_c$ by expressing $\braket{k}$ and $\braket{k^2}$ in terms of the degree exponent and the minimum and maximum degree
	  
	  $$
	  \begin{equation} \begin{split}
	  f_c &= \begin{cases}
	  1-\frac{1}{\frac{\gamma-2}{3-\gamma}k_\text{min}^{\gamma-2} k_\text{max}^{3-\gamma} - 1} & 2 < \gamma < 3 \\ 
	  1 - \frac{1}{\frac{\gamma - 2}{\gamma  -3} k_\text{min} - 1} & \gamma > 3
	  \end{cases} 
	  \end{split}\end{equation}
	  $$

	* Because [[Characterizing Real Networks and Network Phenomena|real networks]] tend to bee finite, we can introduce the relation based on the fact that scale free networks have large hubs. 
	  $$
	  k_\text{max}=k_\text{min} N^{\frac{1}{\gamma-1}}
	  $$
	  
	  This gives a new threshold of 
	  $$
	  f_c \approx 1-\frac{C}{N^\frac{3-\gamma}{\gamma + 1}}{}
	  $$
	  
	  This indicates that *larger networks have thresholds close to the theoretical limit* of $f_c=1$ 

# Enhanced  Robustness 
* A network displays **enhanced robustness** if the breakdown threshold deviates from the breakdown threshold of a  random network . That is 
  $$
  f_c>f_c^{ER}
  $$
  In other words, it has enhanced robustness if *the network performs better than a [[Random Network|randomly]] wired network.*

* This has the following implications 
	* Because $f_c>f_c^{ER}$ for most networks where $\braket{k^2}$ deviates from $\braket{k}(\braket{k} + 1)$, robustness as predicted by the Molloy-Reed criterion 
	* The degree distribution of a network does not need to follow a strict power law to display enhanced robustness.  The only requirement is $\braket{k^2}$ be bigger than a random network of similar size.
	* The critical exponents are dependent on $f_c$
	* Enhanced robustness is not limited to node removal, but emerges from link removal as well.

# Cascading Failures
* Models have been made to capture the dynamics of cascading effects. They share three ingredients.
	* The system is characterized by some [[Flow Network|flow]] over the network 
	* Each component has a local breakdown that determines when it contributes to a cascade 
	* Each system has a mechanism to redistribute the traffic to other nodes on a cascade

## Failure Propagation 
* The **Failure Propagation Model** is a model for cascading failures in a network. 
* In this we consider a network with an arbitrary degree distribution where each node contains an agent that
	* Has some state (active or inactive). Agents are initialized as active. 
	* Is characterized by a breakdown threshold $\phi_i = \phi$
* We proceed as follows 
	* At time $t=0$, set one agent to "inactive". 
	* At subsequent time steps, randomly pick an agent and update its state following a threshold rule:
		* If the selected agent is active, check its neighborhood. 
			* If at least $\phi$ of the neighbors are inactive, then this agent becomes inactive too.
			* Otherwise, it remains active.
		* If the agent was inactive, it remains inactive. 

* Empirical simulations show a phase transition within the model based on $\braket{k}$
	* *Subcritical Region* - If $\braket{k} < 1$, cascades terminate quickly since changes in one node are unlikely to perturb other nodes  and their sizes follow an exponential distribution. 
	* *Critical Region* - If $\braket{k}=1$, the size of the cascades follow a power law distribution. Some cascades are large and some are small 
	* *Supercritical Region* -  If $\braket{k}>1$, the cascades can continue indefinitely, so all cascades are global and the network can experience major breakdowns

## Branching Model
* *This builds on the observation that cascading failures follow a [[Trees|tree]]-like process*. 
* It is a simpler variation of the failure propagation model that works as follows 
	* Start with a single active node 
	* In the next time step, each active node produces $k\sim p_k$ offspring. 
		* If the node selects $k=0$, it will die out 
		* If the node selects $k>0$, it will have $k$ new active sites. 

* We can use the branching model to solve for the size of the cascades empirically. 
* For scale-free networks, it depends on degree exponent $\gamma$. 
  
  Let $\alpha$ denote the exponent of the cascade distribution. We have 
  $$
  \begin{equation} 
  \begin{split}
  \alpha &= \begin{cases}
  \frac{3}{2} & \gamma \ge 2 \\ 
  \frac{\gamma}{\gamma-1} & 2 < \gamma < 3 
  \end{cases}
  \end{split}\end{equation}
  $$
  The fact that this exponent is only dependent on the degree exponent suggests that *the phenomenon of cascades is universal.*

* The critical regions in the branching model largely follow that of the failure propagation model. 
	* *Subcritical Region* - If $\braket{k} < 1$, cascades terminate quickly since changes in one node are unlikely to perturb other nodes  and their sizes follow an exponential distribution. 
	* *Critical Region* - If $\braket{k}=1$, the size of the cascades follow a power law distribution. Some cascades are large and some are small 
	* *Supercritical Region* -  If $\braket{k}>1$, the cascades can continue indefinitely, so all cascades are global and the network can experience major breakdowns
# Designing Robust Networks 
## Designing for Failure
* In order to make a network more robust, *we need to maximize its breakdown threshold*  $p_c$.
* One way to do this is to maximize the average degree, but this also requires us to increase the overall "cost" of the network.
* *We can increase robustness without changing the cost of the network*.
	* By the Molloy-Reed criterion, if we wish to do this for a fixed $\braket{k}$, we should maximize $\braket{k^2}$. 
	* The degree distribution that does this, based on empirical simulations, is a bimodal distribution where the two modes are $k_\text{min}$ and $k_\text{max}$.

* If we wish to optimize the topology against both random failures and attacks  we should maximize  
  $$
  p_c=p_c^{\text{rand}}+p_c^{\text{targ}}
  $$
  By analysis and empirical simulations, this is best achieved with the bimodal distribution 
  $$
  p_k=(1-r)\delta (k-k_\text{min}) +r\delta (k-k_\text{max})
  $$
  The maximum is obtained when $r=\frac{1}{N}$ so that there is only one node that has  $k_\text{max}$ (i.e., there is a hub and spoke topology topology).
  
  The obtained network is robust even under targeted attacks since each of the nodes with degree $k_\text{min}$ are connected to each other. 

## Intervention
* Another approach to build robustness is to make policies for cascading failures. 
* One way to do this is through more links, however in practice this is infeasible since failures can happen much quicker. 
* However, another way to do this is through selective link and node [[Operations on Graphs|removal]]. 
  
  Simulations indicate that *removal should happen right after the initial failure but before it can propagate*.  
  Also, *remove nodes with small loads and links with large excess loads in the vicinity of the initial failure.* 
# Links 
* [[Network Science by Barabasi|Barabasi]]
* [[Fundamental Constructs of Network Science]]

* [[Chegeer's Inequality]] - another measure of robustness. 