* A **Random Graph** is a general term to refer to a [[Random Variables and Probability Distributions|probability distribution]] over graphs. 
# Erdos-Renyi Model
* The **Erdos-Renyi Model** is a model for generating random graphs. We may more formally define Random Networks using two definitions 
	* The $G(N,L)$ model is where the network is chosen [[Probability Distributions Zoo|uniformly]] from a collection of networks with $N$ nodes and $L$ links 
	* The $G(N,p)$ model is here a network of $N$ nodes is generated with probability $p$ of connecting any two nodes 

* In the $G(N,p)$ model, the number of links is given with a binomial distribution 
  
  $$
  p_L={{\frac{N(N-1)}{2}}\choose{L}}p^L(1-p)^{\frac{N(N-1)}{2}-L}
  $$
* The expected value of links is given as 
  $$
  \braket{L}=p\frac{N(N-1)}{2}
  $$

## Evaluation
* *An Erdos-Renyi model has a degree distribution best captured by a Binomial Distribution*, but in practice, it is much more convenient to approximate this using a Poisson Distribution.
	* More specifically if $p$ is the probability that a node ha a link, then 
	  $$
	  p_k={{N-1}\choose k} p^k(1-p)^{N-1-k}
	  $$
	* This can be approximated as 
	  $$
	  p_k=e^{-\braket{k}}\frac{\braket{k}^k}{k!}
	  $$
* In a large random network, the degree of most nodes is in the narrow vicinity of the average degree $\braket{k}$.
# Theorems 
## Theorem on Connectivity 
* A threshold function for the [[Graph Connectivity|connectivity]] is 
  $$
  t(n)=\frac{\ln(n)}{n}
  $$

	* This implies that if $p(n)$ is the link probability and if $p(n)\gg\frac{\ln(n)}{n}$, then the network is connected. 
	* The average degree is 
	  $$
	  \braket{k} \gg \ln (n0 )
	  $$

* A stronger result is as follows. Let $p(n)=\lambda \frac{\ln n}{n}$. Thus 
  $$
  \begin{equation} \begin{split}
  P(\text{connectivity}) &\to \begin{cases}
  0 & \text{if } \lambda <1 \\
  1 & \text{if } \lambda > 0
  \end{cases}
  \end{split}\end{equation}
  $$
* In the first case, it suffices to show that the probability of there being an isolated node goes to $1$.
	* Let $I_i$ be a Bernoulli random variable defined as  
	  $$
	  \begin{equation} 
	  \begin{split}
	  I_i &= \begin{cases}
	  1 & \text{if node } i \text{ is isolated}\\
	  0 & \text{otherwise}
	  \end{cases}
	  \end{split}
	  \end{equation}
	  $$
	* The probability that an individual node is isolated is 
	  $$
	  q=(1-p)^{n-1}\approx e^{-pn} = e^{-\lambda \log (n)}= n^{-\lambda}
	  $$
	  And we use the approximation 
	  $$
	  \left(1-\frac{a}{n}\right)^n=e^{-a}
	  $$
	  Now let $X=\sum_{i=1}^n I_i$ denote the number of isolated nodes. We have the expectation as 
	  $$
	  E[X]=n\cdot n^{-\lambda}=n^{1-\lambda}
	  $$
	  If $\lambda < 1$, we have that $E[X]\to \infty$. We want to show this implies $P(X=0)\to 0$. 
	  
	  Now we may show this using the variance and covariance of $X$. We have that
	  
	  $$
	  \begin{equation} 
	  \begin{split}
	  \text{Var}[X] &= \sum_i\text{Var}[I_i] + \sum_{i} \sum_{j\ne i} \text{Cov}[I_i, I_j] \\
	  &= n\text{Var}[I_1] + n(n-1)\text{Cov}[I_1,I_2]  \\ 
	  &= nq(1-q) + n(n-1)\left(E[I_1I_2] -E[I_1]E[I_2]\right)
	  \end{split}
	  \end{equation} 
	  $$
	  
	* We are able to simplify the second line by the fact that all $I_i$ are identically distributed. The third line follows from the variance of a Bernoulli distribution
	  
	  Continuing we have that 
	  $$
	  \begin{equation} \begin{split}
	  E[I_1 I_2] &= P(I_1 =1, I_2 = 1) \\
	  &= (1-p)^{2n-3} \\ 
	  &= \frac{q^2}{1-p}
	  \end{split}\end{equation}
	  $$
	  We get the full variance of $X$ using the above and the expectation of a Bernoulli distribution 
	  
	  $$
	  \begin{equation}
	  \begin{split}
	  \text{Var}[X] &= nq(1-q) + n(n-1)\left(\frac{q^2}{1-p}-q^2\right)  \\
	  &= nq(1-q) +n(n-1)\frac{q^2p}{1-p}
	  \end{split}\end{equation} 
	  $$
	  Now for large $n$, observe that $q\to 0$ (see its definition above).   That is to say $1-q\to 1$.  Also, we have $p\to 0$ (see the definition of $p(n)$). 
	  
	  It follows 
	  $$\begin{equation} \begin{split}
	  \text{Var}[X] &= nq+n^2q^2 \frac{p}{1-p} \\ 
	  &\sim nq +n^2q^2p \\
	  &= nn^{-\lambda} + \lambda n\ln(n)n^{-2\lambda} \\ 
	  &\sim nn^{-\lambda} \\
	  &= E[X]
	  \end{split}\end{equation}
	  $$
	  So that $\text{Var}[X]\sim E[X]$ which denotes that $\frac{\text{Var}[X]}{E[X]}\to 1$  as $n\to \infty$
	  
	  This implies that 
	  $$
	  E[X]\sim \text{Var[X]}\ge (0-E[X])^2P(X=0)
	  $$
	  Thus rearranging terms gives us that 
	  $$
	  \begin{equation} 
	  \begin{split}
	  P(X=0) &\le \frac{E[X]}{E[X]^2} &= \frac{1}{E[X]} \to 0 
	  \end{split}\end{equation}
	  $$So it follows that there is at least one isolated node, so the graph must be disconnected 

## Theorem on Giant Components 

* A **giant component** is a component of a given random graph which contains a significant fraction of the entire graph's vertices

* A threshold function for the emergence of the giant component of the Erdos-Renyi Model is 
  $$
  t(n)=\frac{\lambda}{n}
  $$
	* If $\lambda < 1$ then all components are small 
	* Otherwise, there is a giant component 
* The giant component emerges if the average degree is $\braket{k} > 1$.
* *This means that as the random network grows, eventually a giant component emerges.*
* In practice [[Characterizing Real Networks and Network Phenomena|real networks are supercritical]]. 

* The **Molloy-Reed Criterion** is a criterion where randomly wired network has a giant component if 
  
  $$
  \kappa =\frac{\braket{k^2}}{k} > 2
  $$
  
	* *Most nodes must be connected to at least two other nodes*
	* For a real network, this  is given as 
	  
	  $$
	  \begin{equation} 
	  \begin{split}
	  \kappa &=\frac{\braket{k^2}}{k} \\
	  &= \frac{\braket{k}(1+\braket{k})}{\braket{k}} \\
	  &= 1 +\braket{k} &> 2 \\ 
	  & \braket{k} &> 1
	  \end{split}
	  \end{equation}
	  $$





# Links 
* [[Network Science by Barabasi]]
* [[Fundamental Constructs of Network Science]]