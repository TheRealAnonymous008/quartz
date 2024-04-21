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

# Impact 
# Links 
* [[Network Science by Barabasi|Barabasi]]
* [[Fundamental Constructs of Network Science]]