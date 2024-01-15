# Degree Distributions 
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
# Links 
* [[Network Science by Barabasi]]
* [[Fundamental Constructs in Graph Theory]]