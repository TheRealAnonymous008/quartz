* The **degree correlation** is a measure of the [[Probability]] of finding a node with degrees $i$ and $j$ at the two ends of a randomly selected link. 
  
  Let $q_k$ be the probability that there is a $k$-degree node at the end of a randomly selected link 
  
  Then 
  $$
  \sum_je_{ij} = q_i
  $$
  $e_{ij}$ is a marginal probability 
	* For [[Directed Graph|directed networks]] we can define variants based on pairings of the in and out degree. 

* The  **degree correlation function** calculates, for all nodes with degree $k$
  
  $$
  k_{nn}(k) = \sum_{k'} k' \ P (k' \mid k)
  $$
	* This can be approximated using the following 
	  
	  $$
	  k_{nn}(k) = ak^\mu
	  $$

* The **degree correlation coefficient** is a constant $r$ defined as 
  
  $$
  r=\sum_{jk}\frac{jk(e_{jk} -q_jq_k)}{\sigma^2}
  $$
  Where
  $$
  \sigma^2=\sum_kk^2q_k- \left[\sum_k kq_k\right]^2
  $$
	* It is the [[Statistical Models|Pearson correlation]] between the degrees found at the two ends of the same link under the assumption of a linear relationship between the degree correlation function and the degree. 


# Classes of Networks
 * An **assortative network** is one where the *hubs tend to link to each other* and avoid linking to small degree nodes.
	* For assortative networks, nodes of comparable degrees tend to link to each other. 
* A **dissassortative network** is a network where *hubs avoid linking with each other*. Instead, they link to small degree nodes. 
	* For disassortative networks, there is a hub and spoke character 
* A **neutral network** is a network whose wiring is *[[Random Network|similar to random]]*.
	* An indicator of this is that the number of links between hubs coincides with what is expected by chance. That is 
	  $$
	  p_{k,k'}=\frac{kk'}{2L}
	  $$
	  Where  
	  $p_{k,k'}$ denotes the probability that a degree  $k$ and $k'$ node link up.
	*  The degree correlation function is given by 
	  
	  $$
	  \begin{equation}
	  \begin{split}
	  P(k' \mid k) &= \frac{e_{kk'}}{\sum_{k'} e_{kk'}} &= q_{k'} \\ 
	  k_{nn}(k) &= \frac{\braket{k^2}}{\braket{k}}
	  \end{split}
	  \end{equation}
	  $$
	* The average degree of a node's neighbor is dependent only on the global network characteristics 

* A **perfectly assortative network** is an extreme case of an assortative network where each degree $k$ only connects with other degree $k$ nodes. 


# Correlations of Various Models 
## Static Models 
* *Models in this category tend to be neutral, and if forced to be simple, exhibit structural disassortativity.*

* The [[Random Network#Erdos-Renyi Model|Erdos Renyi Model]] is neutral by definition 
* The Configuration model is neutral independent of the choice of degree distribution since we allow for multi-edges and loops. 
  
  Any conflict caused by hubs are resolved by the multiple links between them. However, if the network is forced to be simple, then we will encounter structural disassortativity. 
* For a hidden parameter model, the degree correlation is proportional follows
  
  $$
  e_{jk} \propto \eta_j, \eta_k
  $$
	* Here the network is neutral, but forcing it to be simple means encountering structural disassortativity. In such a case, the degree correlation function is 
	  
	  $$
	  k_{nn}(k)\sim k^{-1}
	  $$

## Evolving Networks 
* [[Models for Scale Free Networks#Initial Attractiveness|Initial attractiveness]] - depending on the value of $A$ we observe different scaling regimes. 
	* If $-m<A < 0$ We have a disassortative phase transition where 
  $$
  k_{nn}(k)\sim m\frac{(m+A)^{1-\frac{A}{n}}}{2m+a} \zeta \left(\frac{2m}{2m+A}\right)N^{\frac{A}{2m+A}}k^{\frac{A}{m}}
  $$
  
   It follows a Power Law where $$k_{nn} \sim k^{\frac{|A|}{m}}$$
	* If $A=0$, we have the[[Models for Scale Free Networks#Barabasi-Albert Model|Barabasi-Albert model]] where the network is neutral. We have that
   $$
   k_{nn}(k)\sim \frac{m}{2}\ln N
   $$
   
	* If $A>0$, we have weak assortativity  and
   $$
   k_{nn}(k)\approx(m+A)\ln \left(\frac{k}{m+A}\right)
   $$
   
* For the [[Models for Scale Free Networks#Bianconi-Barabasi|Bianconi-Barabasi]] model with uniform fitness distribution, the network is disassortative due to structural disassortativity. 
	* Analysis shows that the real and the randomized degree correlation functions do not overlap, which means the disassortativity is not fully explained by the network being scale free. 
# Empirical Measurement 
* The use of empirical measurements is useful because analytical methods have their limitations
	* It is difficult to extract information from correlation matrices
	* It is difficult to compare networks with different correlations since magnitude is hard to infer.
	* $e_{jk}$ contains a huge amount of information that is difficult to model.

## Degree Correlation Function
* For a neutral network we have
  
  $$
  k_{nn}=\frac{\braket{k^2}}{k}
  $$
  
  Thus, the average degree of a node only depends on its global characteristics
* For an assortative network, the value of $k_{nn}(k)$ increases with $k$.
* For a disassortative network, the value of $k_{nn}(k)$ decreases with $k$

## Approximate Degree Correlation
* For assortative networks, the parameter $\mu > 0$
* For neutral networks, the parameter $\mu = 0$
* For disassortative networks $\mu < 0$

## Degree Correlation Coefficient.
* For assortative networks, $r < 0$
* For neutral networks, $r=0$
* For disassortative networks $r > 0$.
# Structural Disassortativity
* **Structural Disassortativity** is a phenomenon wherein *a network appears disassortative even though no degree correlation was imposed*
* Because [[Scale Free Network|scale free networks]] have large hubs, there is a natural cutoff for $\gamma$ given by 
  
  $$
  k_{\text{max}} = N^{\frac{1}{\gamma - 1}}
  $$
  
  If $\gamma < 3$ we have that $k_\text{max}$ diverges faster than a neutral network. Thus, an otherwise neutral network may show disassortativity as a result of the structural limitations of the network 
* *For a neutral network, the structural cutoff takes the form* 
  
  $$
  k_s\sim \sqrt{N\braket{k}}
  $$
  If vertices of degree $k\ge k_s$ exist, it is physically impossible to attach enough edges between them to maintain neutrality.
	*  This is apparent in random networks and scale-free networks with $\gamma \ge 3$ 
	* This follows because the correlation is given by 
	  
	  $$
	  e_{kk'}=\frac{kk'p_kp_k'}{\braket{k}^2}
	  $$
	  And the ratio becomes 
	  $$
	  r_{kk'}=\frac{kk'}{\braket{k}N}
	  $$

* There are two ways *we can prevent strucctural disassortativity*
	* Allow multiple edges
	* Remove hubs that have a degree larger than the structural cutoff.
* *We can detect if a degree correlation was a consequence of structural disassortativity* as follows: 
	* Use degree preserving randomization on the original network and check if the generated network exhibits any degree correlations. 
	* If it does, then we have structural disassortativity induced by the degree correlation. 
	* Otherwise, if the real network exhibits correlations beyond the correlations in the generated network, then we have a meaningful property of the network.

# Xalvi-Brunet-Sokolov Algorithm
* The **Xalvi-Brunet-Sokolov Algorithm** generates maximally correlated networks with a predefined degree sequence
* The procedure is as follows
	* *Link selection*. Choose two links at random. Label the four nodes at the end of these two links $a,b,c,d$ such that their degrees are ordered
	  
	  $$k_a\ge k_b\ge k_c\ge k_d$$
	* *Rewiring*. Break the selected links and rewire them to form new pairs depending on which is desired
		* For assortative networks, pair the two highest degree nodes and the two lowest degree nodes.
		* For disassortative networks, the new pairs are $(a,d)$ and $(b,c)$
	* *Iteration*: We iterate over these steps to enhance the assortativity or disassortativity of the network.

* When generating an assortative network, the degree correlation function $k_\text{nn}(k)$ is assortative for small $k$ but disassortative for large $k$ due to the structural cutoff. 
* For scale free networks, the system cannot sustain assortativity for high $k$.
# Impact 
* *The more disassortative the network, the harder it is for the giant component to emerge.*
	* By the [[Random Network#Theorem on Giant Components|Erdos-Renyi theorem on giant components]] and how giant components emerge within random networks, *a giant component emerges in a neutral network when $\braket{k} = 1$. *
	* For assortative networks, the phase moves to a lower $\braket{k}$ (i.e., $\braket{k} < 1$). 
		* However, because hubs tend to link to each other, assortative networks tend to have smaller giant components compared to neutral networks.
	* For disassortative networks, the phase transition moves to higher $\braket{k} > 1$. 

So the giant component emerges at $\braket{k}<1$.
* *Hub removal becomes more impactful the more disassortative the network since hubs are connected to more nodes.*
	* In assortative networks, because the giant component mainly consists of hubs linking with each other, the impact of removing any single hub is low.
	* In disassortative networks, the impact of removing hubs is much higher since each hub tends to connect to many small-degree nodes, which fall off when a hub is deleted
* *Assortative networks have shorter paths on average but larger diameters.*
	* This arises from the fact we connect mostly to nodes with the same degree, so we favor long chains of nodes, each of with have similar degree to their neighbors. 
* *Degree correlation can influence the properties that a network has.*
	* Degree correlations influence the system's stability against stimuli and [[Perturbation Theory|perturbations]].
	* Degree correlations have an impact on the [[The Matching Problem and Flow Networks|Vertex Cover Problem]]
	* Degree correlations impact the ability to control the network. 
# Links 
* [[Network Science by Barabasi|Barabasi]]
* [[Fundamental Constructs of Network Science]]