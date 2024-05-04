* Network epidemics makes use of models that exists within the context of a complex network to extend standard epidemics models. The two primary structures are
	* The **contact network** -- a network that captures quantitative information about the *contacts between two individuals.*
	  
	  Each node corresponds to individuals or entities.
	  
	  Links represent interactions between these individuals
	  
	  Weights may represent quantitative information such as proximity, distance or frequency.

	* The **degree block approximation model** is a variation on the compartmentalization model 
	  
	  In the network, each node is not only classified with a category, but they may also be grouped based on degree.
	  
	  This is based on the assumption that *nodes with similar degrees behave similarly*.

# Epidemics in Networks
* *The network's topology affects the spread of the disease*
	* Nodes which are more connected are more likely to be infected.
	* The degree distribution of the network can determine how the disease will spread.  The spread of a pathogen in a [[Scale Free Network]] is instantaneous. 
	* In instances with recovery, the spread of a disease is affected by the recovery rate and how heterogeneous the network is (i.e., through $\braket{k^2}$)
	* In a scale-free network, the hubs affect the spread of a disease. Hubs cause the virus to instantaneously reach most nodes, and to persist in the population easier even with a small spreading rate. 

* In a [[Network Degree Correlation|neutral network]], the dynamics of the growth of $i_k$ is approximated as 
  
  $$
  \frac{dI_k}{dt}\approx\eta k I_0 \frac{\braket{k}-1}{\braket{k}}e^{t/\tau^{SI}}
  $$
  
  Where $\tau^\text{SI}$ is the characteristic time
  
  $$
  \tau^{SI}=\frac{\braket{k}}{\eta (\braket{k^2} - \braket{k})}
  $$
  The fraction of infected nodes with degree $k$ at time $t$, is then given by the equation
  $$
  I_k=I_0\left(1+\frac{k(\braket{k}-1)}{\braket{k^2}-\braket{k}}\right)\left( e^{t/\tau^{SI}} - 1
\right))
$$

	* The probability a node becomes infected is proportional to its degree.
	* The total fraction of infected nodes not only depends on $\braket{k}$ but also on the second moment $\braket{k^2}$ of the degree distribution
		* For [[Random Network|random networks]], the results are identical to usual homogeneous models (see [[Epidemiology#Homogeneous Models|here]])
		* For [[Scale Free Network|scale free networks]] with degree exponent $\gamma \ge 3$, the dynamics are similar to a random network, except with an altered characteristic time.
		* For scale-free networks with $\gamma \le 3$, the characteristic time vanishes. Thus, the spread becomes instantaneous. 
			* The **Vanishing Epidemic Threshold** occurs during an epidemic because a more scale-free network will have a more instantaneous infection rate. 
			* This is due to how *hubs become superspreaders* that are able to transmit the disease to many parts of the network.

* Introducing a non-zero recovery rate gives the following characteristic time
  $$
  \tau^{SIS}=\frac{\braket{k}}{\eta\braket{k^2}-\mu \braket{k}}
  $$
  For sufficiently large $\mu$ this decays exponentially. However, this decay also depends on the heterogeneity of the network through its second moment.
* For networks, *increasing the spreading rate does not cause a gradual increase in infected*. The pathogen can spread only if the spreading rate exceeds the **epidemic threshold** $\lambda_c$. 
	* For a random network, we obtain that the characteristic time as: 
	  $$
	  \tau ^{SIS}_{ER} = \frac{1}{\eta(\braket{k}+1) -\mu}
	  $$
	  And the epidemic threshold is given as 
	  $$
	  \lambda_c=\frac{1}{\braket{k}+1}
	  $$
	  When $\lambda > \lambda_c$, the pathogen spreads until it reaches an endemic state. 
	* For a network with an arbitrary degree distribution, we have that the threshold is 
	  $$
	  \frac{\braket{k}}{\braket{k^2}}
	  $$
	  In scale free network, for large networks, the epidemic threshold is expected to vanish since $\braket{k^2}\to \infty$ and the epidemic threshold vanishes
	  
	  * As a consequence, the number of infected scales as follows $$\begin{equation} \begin{split}
I(\lambda) &\sim \begin{cases}
\lambda^{1/(3-\gamma)} & 2<\gamma <3 \\ 
2e^{-1/{k_\text{min}}\lambda} & \gamma = 3 \\ 
\left(\lambda - \frac{\gamma - 3}{k_\text{min}(\gamma - 2)}\right)^{1/(\gamma-3)} & 3 < \gamma < 4  \\ 
\lambda - \frac{\gamma -3}{k_\text{min} (\gamma -2)} & \gamma > 4 

\end{cases} 
\end{split}\end{equation}
$$

	* Only for a degree exponent $\gamma > 4$ does a scale-free network behave like a traditional epidemic model.

* In the SIR model, characteristic time is given as 
  $$
  \tau = \frac{\braket{k}}{\eta \braket{k^2} -(\mu+\eta)\braket{k}}
  $$
  The epidemic threshold is given as 
  $$
  \frac{1}{\frac{\braket{k^2}}{\braket{k}}-1}
  $$
* Empirical experiments suggest that *the topology of the contact network is more important when it comes to determining the spread of a contagion than the secondary parameters of the epidemic*.
# Models
## Standard
* The dynamics of the model evolve differently for each degree block
  
  $$
  \frac{dI_k}{dt} = \eta \ (1-I_k) k\ \Theta_k - \mu I_k
  $$
* In the SIR model, the equations become 
$$
\begin{equation} 
\begin{split}
\frac{dI_k}{dt}&=\eta S_k\Theta_k-\mu I_k\\
S_k&= 1-I_k-R_k 
\end{split}
\end{equation}
$$
## Temporal Networks
* A **temporal network** is a network whose links are only active in certain periods of time. Each link carries information on when it's active, along with other possible characteristics such as weight.
* This extension follows from how *nodes do not interact all the time*. Ignoring this fact means we overestimate our results.
	* Interevent times in a temporal network, based on empirical studies, follow a power law. *Individuals have frequent bursty interaction within a short time-frame, and very long time gaps between two contacts.*
	* Interevent times increases the characteristic time and the number of infected individuals decays slower. 

## [[Network Degree Correlation|Degree Correlation]]
* Calculations indicate that degree correlations affect the spread of a pathogen by altering the speed with which a pathogen spreads.
* *Assortative networks decrease the epidemic threshold, while disassortative networks increase it*. In disassortative networks, hubs are infected faster.
* Assortative correlations lower the prevalence, but increase the average lifetime of an epidemic outbreak. This is because the hubs remain infected. 

## Link Weights
* Links are not necessarily equal within the contact network. 
* Tie strengths in real networks vary considerably, and this heterogeneity plays an important role in spreading phenomena. *The more time a individual spends with an infected individual, the more likely they become infected .*

## [[Network Communities|Communities]]
* *The existence of communities lead to repeated interactions between nodes of the same community. *
* By the community hypothesis, communities tend to have stronger ties together. This implies the following
	* Once a contagion reaches a community member, it can rapidly reach all the other members of the same community.
	* A simple contagion has a harder time escaping communities since communities tend to have weak ties between each other. 
	* A strong contagion can be reinforced and incubated due to the strong ties within communities. Thus, the contagion can spread much faster. The contagion becomes viral  if it can spread to multiple communities. 

# Immunization
* In random networks, we consider the following
	* If If the pathogen spreads on a random network, for a sufficiently high immunization fraction, the spreading rate could fall below the epidemic threshold.
	  
	  We do this with **immunization rate** $g_c$ calculated as 
	  
	  $$
	  \frac{(1-g_c)\eta}{\mu}= \frac{1}{\braket{k}+1}
	  $$
	  
	  *This shows why vaccination is useful.* The characteristic time becomes negative and the contagion dies out.

	* If the pathogen spreads on a network with high $\braket{k^2}$, we have to have
	  $$
	  \frac{\mu}{\beta}(1-g_c)=\frac{\braket{k}}{\braket{k^2}}
	  $$
	  This implies that for networks with high second moments, *we need to randomly vaccinate virtually all nodes*.. Because of the power law distribution, this applies to scale-free networks (and most [[Characterizing Real Networks and Network Phenomena|real networks]])

* For scale free networks, we can also reduce $\braket{k^2}$ by performing **hub immunization**.
	* This follows because *hubs are the source of heterogeneity in the  network*. Hub immunization increases the epidemic threshold
	* This is analogous to [[Network Robustness|doing a targeted attack on the contact network]]. In fact, this works because scale free networks have low attack tolerance. 
	* Implementing this requires knowledge of the contact network, so in practice this is difficult to do. However, we can use [[Characterizing Real Networks and Network Phenomena|the friendship paradox]]
		* Randomly sample an individual in the network.
		* Immunize the neighbors of the individual. The friendship paradox suggests we will target hubs without knowing precisely who are hubs. 
# Links
* [[Network Science by Barabasi|Barabasi]]
* [[Fundamental Constructs of Network Science]]
* [[Epidemiology]]