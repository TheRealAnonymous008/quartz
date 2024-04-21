* The **Small World Property**  is a network property that holds when the average distance $\braket{d}$ grows proportionally to the logarithm of the number of nodes $N$ in the network. That is
  $$
  \braket{d}\propto\frac{\ln N}{\ln\braket{k}}
  $$

	* Intuitively, the above simply says that in a network with the small world property, a *typical path will consist of only a few nodes compared to the size of the network*. 
	* Also, the above relation captures the fact that for dense networks where $\braket{k} \gg 1$, the average path length is lower.

## Derivation of the Small World Property 
* We are motivated by the fact the expected number of nodes up to the distance $d$ from our starting node is obtained by the geometric series 
  $$
  N(d)\approx 1+\braket{k}^2+\dots+\braket{k}^d = \frac{\braket{k}^{d+1} - 1}{\braket{k}-1}
  $$
  Note that $N(d)\le N$, thus the distances have a maximum $d_\text{max}$ such that 
  $$
  N(d_\text{max})\approx N
  $$
  And if $\braket{k}\gg 1$, we may simplify the geometric sum above as $$\begin{equation} \begin{split}
N(d_\text{max})&\approx N  \\ 
&\approx \braket{k}^{d_\text{max}}
\end{split}\end{equation}
$$And we derive the small world property using $d_\text{max}$
$$
d_\text{max}=\frac{\ln N}{\ln \braket{k}}
$$
* In practice, $d_\text{max}$ above may be reinterpreted as the average distance since for most networks, the actual maximum distance is dominated by a few extremal paths, whereas $\braket{d}$ is averaged  over all nodes in the network. Thus, in actuality, the small world property is that $$\braket{d}\propto\frac{\ln N}{\ln\braket{k}}$$
## Small World Networks 
* A **small world network** is a network for which the *small world property holds and for which average clustering is high.*
* It can be described as an interpolation between a regular network and a [[Random Network|random network]]. As such, it can be seen that it has a [[Probability Distributions Zoo|Poisson degree distribution]] since high degree nodes remain absent from it. 
* This emerges, for example, as **Six Degrees of Separation**, wherein we may connect any two nodes in a (social) network using a path of only six vertices. 
* *Note*: [[Characterizing Real Networks and Network Phenomena|Real networks are not Poisson]] so most real networks are not small world networks .

## Ultra Small World 
* A network has the **ultra small world property** if the average distance grows significantly slower than a regular small world network. 

# Watts-Strogatz Model 
* The **Watts-Strogatz Model** is a model for generating a small world network 

* We may generate a small network via the Watts-Strogatz model as follows.
	1. Start with a ring of nodes, each node connected immediately to their neighbors.  
	2. With a *rewiring probability* $p$, we may choose to reconnect each link to a new pair of endpoints.
* Effectively, then, the  average distance and the average clustering coefficient depend on the rewiring probability $p$.

![[Watts-Strogatz.png]]
# Links 
* [[Fundamental Constructs of Network Science]]
* [[Network Science by Barabasi|Barabasi]]