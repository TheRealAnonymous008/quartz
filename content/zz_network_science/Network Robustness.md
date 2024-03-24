* The breakdown of a complex [[Fundamental Constructs of Network Science|network]] is not gradual. Removing a small number of nodes only has a limited impact on integrity, but once a fraction of removed nodes reaches a critical threshold, the network abruptly breaks into disconnected components. 
	* *Random node failures induce a phase transition* from a [[Graph Connectivity|connected]] to disconnected network. 
	* [[Percolation Theory]] is applicable mostly for random and regular networks 
# Random Networks 
* Let $f$ be the fraction of nodes that were removed in an inverse percolation process. 
  
  For sufficiently large $f$, we break the [[Random Networks#Theorem on Giant Components|giant component]] in the network. In this sense, we can use an inverse percolation process to understand the robustness of a network.
  
* As it turns out, the fragmentation of the network is not gradual, but characterized by a  threshold function determined by coefficient $f_c$.
  
  If $f<f_c$, then the giant component persists. However, once $f>f_c$, the giant component vanishes. 
  
  This is illustrated by the dependence on $f$ of the order parameter 
  
  In fact, we can analyze $f$ using the same  critical exponents  for the order parameter, correlation length and average cluster size This can be done by setting $f=1-p$.

# Scale Free Networks 
* Following an inverse percolation process during a breakdown, scale-free networks tend to have their largest component decrease in size gradually, vanishing in the vicinity of $f=1$ 
* This implies that scale-free networks have an unusual robustness to random node failures, which is different from the collapse of random networks (see [[#Random Networks|above]]).
* Intuitively, *the robustness of a [[Scale Free Networks]] against random attacks comes from the fact that many nodes are of small-degree, and these do not impact the overall connectivity of the network.*

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
  In other words, it has enhanced robustness if *the network performs better than a randomly wired network.*

* This has the following implications 
	* Because $f_c>f_c^{ER}$ for most networks where $\braket{k^2}$ deviates from $\braket{k}(\braket{k} + 1)$, robustness as predicted by the Molloy-Reed criterion 
	* The degree distribution of a network does not need to follow a strict power law to display enhanced robustness.  The only requirement is $\braket{k^2}$ be bigger than a random network of similar size.
	* The critical exponents are dependent on $f_c$
	* Enhanced robustness is not limited to node removal, but emerges from link removal as well.
# Links 
* [[Network Science by Barabasi|Barabasi]]