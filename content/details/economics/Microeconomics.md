* The **Invisible Hand** dictates that economies are generally predictable even if they are [[Complex Systems]]. 
	* This holds for as long as two principles hold 
		* That there is enough competition among buyers and sellers 
		* That all agents in the economy operate with [[Game Theory|rationality]]. 
	* It also suggests that Pareto optimality can be achieved even among selfish agents [^opp_2]
	* *Supply and demand reveal themselves through the behaviors of producers and consumers.*

[^opp_2]: See more [[Static Games of Incomplete Information|here]]. Incomplete information and uncertainty also helps. 

* *All choices are governed by [[Trade Offs|tradeoffs]] due to scarcity of resources*
* Every market is more or less subject to the laws of supply and demand. We can analyze the dynamics of the market using a four step process that analyzes the relationship between the two. 
	* Identify the supply and demand curves and the equilibrium point
	* Decide whether the economic change affects supply and demand 
	* Decide how it affects supply or demand (does it induce a shift to the right or the left) . If there are multiple variables and effects, analyze each individually. 
	* Compare the new equilibrium to the old equilibrium

# Misc
* Consider an economic system with $n$ agents and $m$ resources. 
  
  Assume we have a price vector $p\in \mathbb{R}^{+m}$ corresponding to the price of each commodity, and an allocation matrix $x$ where $x_{ij}$ represents the amount of resource $j$ allocated to agent $i$.
  
  Each agent also has an endowment $e_i\in\mathbb{R}^m$ and a utility function $u_i : \mathbb{R}^m\to \mathbb{R}$
  
  The **Competitive (Walrasian)** equilibrium $(x^\ast, p^\ast)$ satisfies the following properties. 
	* The allocation is feasible  $\forall j$:  
	  $$
	  \sum_i x_{ij}^\ast \le \sum_{i} e_{ij}
	  $$
	* All agents maximize their utilities under the budget induced by the prices. $\forall i$
	  $$
	  x_i^\ast = \underset{x_i\in[0,1]^m}{\text{argmax}}  \ u_i(x_i) \ \ \ \ \ \text{subject to } p^{\ast T}x_i \le p^{\ast T} e_i
	  $$

# Topics 
* [[Scarcity, Supply, and Demand]]
* [[Consumer Behavior and Transactions]]

* [[Firms, Production and Externalities]]
* [[Competition between Firms]]
* [[Labor Market Theory]]
* [[Financial Market]]
* [[Public Economy]]

# Links  
* [[Principles of Economics by Shapiro, MacDonald and Greenlaw]]
* [[Thinking Fast And Slow]]  - helps in understanding why people act the way they do. 