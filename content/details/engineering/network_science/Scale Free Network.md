* A **scale free network** is a network whose degree distribution *follows a power law*. The term scale-free comes from how power laws are scale invariant 
* Most models under [[Preferential Attachment]] can generate scale-free networks
* We have several [[Models for Scale Free Networks ]]
# Properties 
## Large Hubs 
* In a large scale-free network, t*he biggest hubs are orders of magnitude larger than the smallest nodes in the networks.*

* Let us use the  natural cutoff of the continuous power law distribution of a scale-free network.
  
  We have the following distribution 
  $$
  p(k)=(\gamma-1)k_\text{min}^{\gamma - 1}\ k^{-\gamma}
  $$
  
  
  Let us assume that in a network of $N$ nodes, we expect at most one node that has degree bigger than $k_\text{max}$. 
  
  We, therefore, have that
  $$
  \int_{k_\text{max}}^\infty p(k)dk=\frac{1}{N}
  $$
  Or expanding the integral
  $$
  \int_{k_\text{max}}^\infty (\gamma-1)k_\text{min}^{\gamma - 1}\ k^{-\gamma} dk=\frac{1}{N}
  $$
  Which, when evaluated gives
  $$
  k_\text{max}=k_\text{min} N^{\frac{1}{\gamma-1}}
  $$
  This implies that $k_\text{max}$ has a polynomial dependence on $N$, so large scale-free networks have disproportionately large hubs.

## Low Attack Tolerance 
* For scale free networks , there is a *phase transition at  an incredibly low value for targeted [[Network Robustness|attacks]]*. This is because hubs  play an important role in keeping the network connected. 
  
  It only takes the removal of a few hubs for the network to fragment.

* Within a network, the [[Operations on Graphs|removal]] of a single node is unlikely to fragment the network  However, targeted attacks  can disconnect the network and cause it to break down into tiny clusters. 
* The [[Network Robustness#Scale Free Networks|robustness of scale free networks ]] , combined with the modifications of an attack on a scale free network give us that the breakdown thresholds for attacks on a scale-free network is the solution to this
  $$
  f_c^{\frac{2-\gamma}{1-\gamma}}=2+\frac{2-\gamma}{3-\gamma} k_\text{min}\left(f_c^{\frac{3-\gamma}{1-\gamma}} - 1\right)
  $$

* We can make the following observations
	* $f_c$ increases for small degree exponents and decreases for large degree exponents.
	* $f_c$ for attacks is always smaller than that for random failures.
	*  For large $\gamma$, the scale free network behaves like a [[Random Network|random network]] under attack. At large $\gamma$, the attack and failure thresholds converge to each other and they become indistinguishable.


## Thresholds 
* The degree exponent introduces a threshold on the scale-free network. in particular on the average distance
  
  We have that
  $$
  \begin{equation} \begin{split}
  \braket{d} &= \begin{cases}
  \text{const} & \gamma =2 \\
  \ln\ln N & 2<\gamma <3 \\
  \frac{\ln N}{\ln\ln N}
  & \gamma = 3 \\
  \ln N & \gamma > 3 
  \end{cases}
  \end{split}
  \end{equation}
  $$
  
  
* We may see that the scale-free property has the following characteristics.
	 * Smaller average path lengths since hubs act as bridges between many nodes.
	 * Networks become ultra-small. The smaller the degree exponent $\gamma$, the shorter the distances between the nodes.
	 * If $\gamma >3$, the scale-free network now exhibits the same properties as a small-world network.
	 * If $2 <\gamma < 3$, the giant component emerges (see [[Random Network#Theorem on Giant Components|here]]). 

### Anomalous Region  $\gamma = 2$
* By the calculations [[#Large Hubs|here]], we find that when $\gamma = 2$,
  $$
	  k_\text{max}=k_\text{min}N
	  $$
	  
  This forces the network to have all nodes be close to each other, and so the average distance is independent of $N$.
  
* This region is anomalous, because the average degree diverges as $N\to \infty$. But also, the largest hub must connect to more nodes than there are links in the network. 
* Thus, large scale-free networks with $\gamma < 2$ that lack multiple edges cannot exist. 

### Ultra-Small World  ##
* This region is characterized by being  [[Small World Networks|Ultra small]] since $\ln\ln N$ grows much slower than $\ln N$. 

* This is indicative of the fact that hubs significantly reduce the distance between any two nodes. 
* In this case, $k_\text{max}\propto N^{\frac{1}{\gamma - 1}}$, where $\frac{1}{\gamma -1} < 1$ so the proportion of nodes connected to the largest hub decreases as 
$$
\frac{k_\text{max}}{N}\propto N^\frac{-(\gamma-2)}{\gamma - 1}
$$

### Critical Point $\gamma = 3$
* At $\gamma = 3$, we encounter a critical point where the dependence to $\ln N$ returns, yet this is corrected by the presence of $\ln \ln N$. This means, that it is on the verge of displaying the small world property

### Small World 
* Here, we find the network satisfies the small network property. 
* While hubs remain, they are not sufficiently large or numerous to have a significant impact on the distance between nodes.
* For all intents and purposes, the properties of a scale-free network here are hard to distinguish from that of a small-world network. In theory, however, we can achieve this by having 
  $$
  N\ge \left(\frac{k_\text{max}}{k_\text{min}}\right)^{\gamma -1}
  $$
  In practice, no real network is that big. 


## Percolation 
* The [[Percolation Theory|critical exponents]] of a scale-free network are determined as follows. 

* The average cluster size near $p_c$ follows 
  
  $$
  \begin{equation} 
  \begin{split}
  \gamma_p &= 
  \begin{cases}
  1 & \gamma > 3 \\ 
  -1 & 2 < \gamma < 3
  \end{cases}
  \end{split}
  \end{equation}
  $$
  This emerges due to the [[#Thresholds|Average distance thresholds]]. 

* The order parameter critical exponent $\beta$ is given by 
  
  $$
  \begin{equation}
  \begin{split}
  \beta_p &= 
  \begin{cases}
  \frac{1}{3-\gamma} & 2 <\gamma < 3 \\
  \frac{1}{\gamma -3} & 3 < \gamma < 4 \\ 
  1 & \gamma > 4
  \end{cases}
  \end{split}
  \end{equation}
  $$
	* In a scale-free network, *the giant component collapses faster around $p_c$ than a random network*.

* The average size off the finite components is given by 
  
  $$
    \begin{equation}
  \begin{split}
 v &= 
  \begin{cases}
  \frac{\gamma-3}{\gamma - 2} & 3 <\gamma < 4 \\
  \frac{3-\gamma}{\gamma -2} & 2 < \gamma < 3 \\ 
  \end{cases}
  \end{split}
  \end{equation}
  $$

# Links 
* [[Network Science by Barabasi|Barabasi]]
* [[Random Network]]
* [[Fundamental Constructs of Network Science]]