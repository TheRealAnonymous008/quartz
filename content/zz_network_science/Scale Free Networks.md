
* Most models under [[Preferential Attachment]] can generate scale-free networks
# Barabasi-Albert Model 
* The **Barabasi-Albert Model** is a minimal model that can generate a scale-free network. It consists of two aspects 
	* **Growth** - At each time step, add a new node to the network with $m$ links that connect the new node to $m$ nodes already in the network.
	* **Preferential Attachment** 

* *Assume*:
	* The probability to connect to a node depends on that node depends on that node's degree.
	* $\Pi(k)$ is linear in $k$.

## Properties 
* The degree distribution is given as 
  $$
  p(k)=\frac{2m(m+1)}{k(k+1)(k+2)}
  $$
	* For large $k$, the above reduces to $k^{-3}$ in line with that shown in scale-free networks 
	* The power law that emerges is independent of the choice of $m$
	* The power law distribution is scale and time invariant, which can also be observed in the above distribution of the Barabasi-Albert model 
	* The coefficient of the power-law distribution is proportional to $m(m+1)$, which is supported by numerical simulations.
	* Derivation is given in [[Network Science by Barabasi|Barabasi Box 5.3]] 

* The Barabasi-Albert model tends to be *more clustered than a random network* The average clustering is obtained as 
  
  $$
  \braket{C} = \frac{(\ln N)^2}{N}
  $$

##  Evaluation 
* The degree distribution of the Barabasi-Albert Model implies the following about the structure of the model 
	* A *power law emerges* of independent of the links per node in the growth 
	* The power law that emerges provides supporting evidence that the Barabasi-Albert model gives a scale-free network.

* *Growth and Preferential attachment are necessary to model most real networks*, so indeed, the model captures this aspect of real networks.
	* Without growth, the network will eventually become a complete graph with a non-power law degree distribution 
	* Without preferential attachment, the degree distribution shows exponential decay, which means that the network lacks hubs .

* Because of growth and preferential attachment, hubs are large and get larger as the number of nodes increases. 
* In a Barabasi-Albert model, *older nodes in the network are more likely to grow than newer networks.* This explains where our hubs come from.
	* In the model, an existing node can increase its degree when a new node enters the network. This node will link to $m$ of the $N(t)$ nodes in the network. The link probability is given as $\Pi$. 
	* If we approximate the degree $k_i$ as a real variable, representing the [[Random Variables and Probability Distributions|expected value]] over the growth process, the rate at which an existing node $i$ acquires links is 
	  $$
	  \frac{dk_i}{dt}=m\Pi(k_i)=m\frac{k_i}{\sum_{j=1}^{N-1} k_j}
	  $$
	* Because the denominator goes over all nodes except the newly added one, the sum is equal to $2mt-m$ and so 
	  $$
	  \begin{equation} \begin{split}
	  \frac{dk_i}{dt}&=\frac{k_i}{2t-1}  \\ 
	  &\approx \frac{k_i}{2t}
	  \end{split}\end{equation}
	  $$

	* Using the fact that $k_i(t_i)=m$ (i.e., node $i$ joins the network at $t_i$ with $m$ links), we obtain 
	  $$
	  k_i(t)=m\left(\frac{t}{t_i}\right)^\beta
	  $$

	* Where $\beta$ is referred to as the **dynamical exponent**. Here it has value $\frac{1}{2}$. This implies that the degree exponent is $\gamma = 2$.
	* The degree of each node increases following the power law. *Older nodes eventually become hubs*.


* The Barabasi-Albert network features *shorter distances between nodes*.
  
  The diameter when $m>1$ and large $N$ is given by 
  
  $$
  \braket{d}\sim \frac{\ln N}{\ln \ln N}
  $$

* The [[Random Networks#Theorem on Giant Components|Molloy-Reed Criterion]] on a scale-free network to get a [[Percolation Theory|breakdown threshold]] $f_c$, we arrive at 
  
  $$
  f_c = 1-\frac{1}{\frac{\braket{k^2}}{\braket{k}}-1}
  $$

# Extensions 
## Linearized Chord Diagram 
* Aims to make the Barabasi-Albert model more rigorous by modifying the generation algorithm. 
	* Start with $G_1^{(0)}$ which is a graph with no nodes. 
	* Given $G_1^{(t-1)}$, generate $G_1^{(t)}$ by adding node $v_t$ and a single link between $v_t$ and $v_i$ with link probability 
	  $$
	  \begin{equation} \begin{split}
	  p &= \begin{cases} 
	  \frac{k_i}{2t-1} & \text{if } 1 \le i \le t-1  \\ 
	  \frac{1}{2t-1} & \text{if } i = t
	  \end{cases} 
	  \end{split}
	  \end{equation}
	  $$
	  This allows for loops and multi-edges however, this number becomes negligible at the limit 

	* For $m > 1$, build $G_m^{(t)}$ by adding $m$ links from the new node $v_t$ one by one. In each step, we allow the outward half of the newly added link to contribute to the degrees.
	  
	  That is, when a new node attaches to an existing node, increment the existing node's degree by one.

## Bianconi-Barabasi
* The **Bianconi-Barabasi Model** adds a criterion of fitness to each node 
	* The growth of a network follows by adding a new node $j$ with $m$ links and fitness $\eta_j$. 
	* The **fitness** pertains to an intrinsic property of nodes that propels them ahead of other nodes when the network grows 
	* The fitness is chosen from a fitness distribution $\rho(\eta)$, and this fitness does not change.
	* Preferential attachment is obtained by having the link probability be determined by both the fitness and the degree of the node as shown 
	  
	  $$
	  \Pi_i=\frac{\eta_i k_i}{\sum_{j} \eta_j k_j}
	  $$

* There is, in fact, a *dependence between the degree distribution and the fitness distribution* of each node in the Bianconi-Barabasi model. More specifically we have that [^biabar_1]
  $$
  p_k\approx C \int d\eta \frac{\rho(\eta)}{\eta} \left(\frac{m}{k}\right)^{\frac{C}{\eta} + 1}
  $$

[^biabar_1]: See [[Network Science by Barabasi|Barabasi]] Ch. 6.1

* In a fitness-model, *nodes with higher fitness will increase in degree faster.* Thus, it is not enough to be the "oldest" node in the  network. Newer nodes which are very fit can easily grow quicker given enough time.
	* In particular, the degree exponent of the Bianconi-Barabasi model satisfies [^biabar_1]
	  
	  $$
	  \begin{equation} \begin{split}
	  \beta(\eta) &= \frac{\eta}{C} \\
	  C &= \int \rho(\eta)\frac{\eta}{1-\beta(\eta)}d\eta
	  \end{split}\end{equation}
	  $$


## Accelerated Growth 
* The **Accelerated Growth Model** extends the assumption that the number of links increases linearly with the number of nodes.
* In real networks, *accelerated growth is observed where the number of nodes grows faster than linearly.* 
* Accelerated growth makes the network more homogeneous. It may lead to **hyper-accelerating growth** where the average degree grows linearly with time and the network no longer becomes scale-free 
* Assume that in a growing network, the number of new links arriving with each new node is 
  $$
  m(t)=m_0t^\theta
  $$
  The degree exponent now changes to 
  $$
  \gamma = 3 + \frac{2\theta}{1-\theta}
  $$
  If $\theta=1$, then the average degree diverges. 

## Aging 
* The **Aging Model** accounts for the fact that *some nodes in the system might only persist for a limited time*. 
* In practice, aging is due to the finite amount for resources that nodes may consume.

* The preferential attachment is given as
  $$
  \Pi(k_i,t-t_i) \sim k(t-t_i)^{-v}
  $$
  Where $v$ affects the dependence of the incoming node on the age of existing nodes.
  * If $v<0$, new nodes will link to older nodes. Hence, aging will actually enforce the scale-free property. 
  * If $0<v<1$ new nodes will link to younger nodes. This will homogenize the network.
  * If $v>1$ the aging effect will overcome the preferential attachment, leading to the loss of the scale-free property

## Initial Attractiveness
* The **initial attractiveness model** addresses a limitation of the Barabasi-Albert model wherein isolated nodes cannot acquire links
* The Preferential Attachment is modified to be of the form 
  
  $$
  \Pi_k \sim A+k
  $$

* $A$ denotes the initial attractiveness which indicates the probability that it acquires its *first link in the next time step. *

## Internal Links 
* The **internal links model** adds the phenomenon of *double preferential attachment* that can affect the homogeneity of the degrees in the network.
* We make use of double preferential attachment, where for internal nodes we have that 
  
  $$
  \Pi(k,k')\sim(A+Bk)(A+Bk')
  $$

* Double preferential attachment has the following effects:
	* If $A=0$, then the degree exponent lowers which *makes the network more heterogeneous* by connecting hubs together and making them larger. Here the degree exponent becomes 
	  $$
	  \gamma=2+\frac{m}{m+2n}
	  $$

	* If $B=0$ we have the case of *random attachment* which increases the degree exponent and makes the network more like a random network 
	  
	  $$
	  \gamma=2+\frac{m}{m+2n}
	  $$
## Node Deletion 
* The **Node Deletion** accounts for the fact that *some nodes can be deleted or removed while others may be virtually impossible to remove*. 
* The scale-free property of networks can persist even with node deletion as long as the rate of adding new nodes is greater than the rate of removing them.

* Node deletion causes the growth in three phases 
	* In the *Scale-Free Phase* the number of nodes removed is smaller than the number of new nodes. Thus, the network continues to grow with the degree exponent. 
	  
	  $$
	  \gamma = 3+\frac{2}{1-r}
	  $$
	  $r>1$ 

	* In the *Exponential Phase*, the rate of node removal  is the same as the rate of node arrival. Thus, the network has a fixed size, and will lose its scale free nature.
	* In the *Declining Phase*, the rate of node removal exceeds the number of new nodes. 
# Links 
* [[Network Science by Barabasi|Barabasi]]
* [[Random Networks]]
* [[Fundamental Constructs of Network Science]]