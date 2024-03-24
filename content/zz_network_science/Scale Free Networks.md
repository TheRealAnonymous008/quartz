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
	*  For large $\gamma$, the scale free network behaves like a [[Random Networks|random network]] under attack. At large $\gamma$, the attack and failure thresholds converge to each other and they become indistinguishable.


# Thresholds 
* The degree exponent introduces a threshold on the scale-free network. 


 


# Links 
* [[Network Science by Barabasi|Barabasi]]
* [[Random Networks]]
* [[Fundamental Constructs of Network Science]]