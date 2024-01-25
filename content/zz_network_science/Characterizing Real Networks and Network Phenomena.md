# Real Networks 
## Degree Distributions 
* In real networks we can observe the following properties in their degree distributions 
	* **Low Degree Saturation** -  It can be see as a flattened $p_k$ for $k<k_{\text{sat}}$. This indicates that we have *fewer small degree nodes than that is expected from a power law.
	* **High Degree Cutoff** - This manifests as a rapid drop in $p_k$ for $k>k_\text{cut}$. Effectively, this indicates that t*he largest hub is smaller than predicted in the power law.* 
		* This emerges if there are inherent limitations in the number of links the nodes can have.

* Deviations from the power law imply that 
  $$
  p_k=\alpha(k+k_\text{sat})^{-\gamma} \exp\left(-\frac{k}{k_\text{cut}}\right)
  $$
  Where 
  $k_\text{sat}$ denotes the saturation cutoff 
  $k_\text{cut}$ denotes the high degree cutoff.

* *Real networks do not have a degree distribution that is [[Probability Distributions Zoo|Poisson]]*  (see [[Network Science by Barabasi|Barabasi]] Ch. 3.5)
	* The probability of observing a node with large degree decreases exponentially given as 
	  $$
	  p_k=\frac{e^{-\braket{k}}}{\sqrt{2\pi k}}\left(\frac{e\braket{k}}{k}\right)^k
	  $$
	* The bounds of the degree cutoff is given with a probability distribution 
	  
	  $$
	  1-P(k_\text{max}) \approx e^{-\braket{k}}\frac{\braket{k}^{k_\text{max}+1}}{k_\text{max}+1}
	  $$

## Non-Alignment with Random Networks
* *Real Networks are not random*.  [[Random Networks]] do not capture certain things in practice. 
	* Real Networks are not Poisson 
	* The average clustering coefficient of a random network is different to the average clustering coefficient in a network. *In real networks, the average clustering coefficient is related to the degree of the node*, which is not the case for random networks. 
	* The connectedness of a Random Network is different from how it is in practice. The condition in [[Random Networks#Theorem on Connectivity|Erdos-Renyi's Theorem on Connectivity]] does not hold for real networks.

* *Real networks are sparse*. That is, they have significantly less links than the theoretical maximum. [^sparse]

[^sparse]: In practice, this means that storing a network can be done using [[Linear Algebra|sparse matrices]]. 

* *Real networks are supercritical*. Real networks have giant components. By [[Random Networks#Theorem on Giant Components|Erdos-Renyi's Theorem on Giant Components]], in a real network $\braket{k} > 1$. 
	* Most real networks are not connected, in which case the giant component co-exists with other smaller components. 
	* Erdos-Renyi's Theorem on Connectivity suggests that 
	  $$
	  \braket{k} < \ln(N)
	  $$

## Robustness
# Network Phenomena 
* *Many real networks are [[Scale Free Networks]]* which results in some interesting properties 
	* The fact that *many real networks are scale free* means most real systems have "centers of interest" (i.e., hubs).  These hubs are a double edged sword, they provide connectivity to the system, while also introducing vulnerabilities such as being superspreaders of pathogens.
	* However, *not all real networks are scale-free*.. In particular, the networks of material sciences, and the network of power grids do not appear to follow the scale-free property.
	* It appears that, *for the scale-free property to emerge, nodes need to have the capacity to link to other nodes*. Otherwise, the scale-free property is absent in a system that limits the number of links a node can have (i.e., in a scenario where [[System Archetypes|there are limits to growth]])
	* The **Matthew Effect** is the tendency of individuals to accrue social or economic success in proportion to their initial level of success.  *The rich get richer and the poor get poorer*.

* **Metcalfe's Law** states that *the value of a network is proportional to the square of the number of nodes in the network.*
	* *The more individuals use a network, the more valuable it becomes.
	* The value of a service is proportional to the number of connections it can create. A service becomes profitable as a result if the number of connections surpasses the number of nodes. 
	* Some limitations of this law: 
		* Most real networks are sparse which means that actually the value only grows linearly rather than quadratically.
		* If the network is weighted, then not all links are of equal value.
		  
	  ![[Metcalfe's Law.png]]
# Links 
* [[Network Science by Barabasi]]
* [[Fundamental Constructs of Network Science]]