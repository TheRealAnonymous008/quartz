* **Percolation Theory** describes the behavior of a [[Network Science|network]] when nodes or links are [[Operations on Graphs|added]]. 
* A **percolation** is a process wherein given a lattice, we place pebbles with probability $p$ at each lattice point. Neighboring pebbles are considered connected. 
	* An **inverse percolation process** involves removing nodes instead of adding them from the lattice. 
* The **percolating cluster** is an emergent property during a percolation process. 
	* We may define a threshold function, where, when $p\to p_c$, we go from a system of tiny clusters to one having a giant cluster. $p_c$ is the *breakdown threshold*.  

# Fundamental Quantities 
* The **breakdown threshold** is a threshold notated $p_c$. It is the number of nodes that is needed for a given network to have a percolating cluster. 


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

## Critical Exponents
* In a percolation process the **average cluster size** is defined as $$\braket{s}=|p-p_c|^{-\gamma_p}$$Where
	  $p_c$ is the breakdown threshold 
	  $\gamma_p$ is the critical exponent.
	  As $p\to p_c$ this value diverges 

* The **order parameter** is a parameter that dictates the [[Probability]] that a randomly chosen pebble in a percolation process belongs to the largest cluster. 
  
  It is notated $p_{\infty}$ and follows $$p_\infty \sim (p-p_c)^{\beta_p}$$Where  $\beta_c$ is the critical exponent.
	* As $p\to p_c^-$, this probability drops to $0$.

* In a percolation process, the **correlation distance** is the mean distance between two pebbles in the same cluster. It is defined as 
  
  $$
  \xi \sim |p-p_c|^{-v}
  $$
  Where $v$ is a critical exponent .
	* As $p\to p_c$, the distance goes from  finite to divergent.  This implies the size of the largest cluster becomes infinite and percolates the whole lattice.

* The **critical exponents** are a set of three exponents that describe a percolation process 
	* $\gamma_p$ - average cluster size 
	* $\beta_p$ - order parameter 
	* $v$ - correlation length 
* *In a percolation process, the critical exponents are universal properties which are independent of the precise value of $p_c$ or the lattice*. 

# Links 
* [[Network Science by Barabasi|Barabasi]]
* [[Fundamental Constructs of Network Science]]