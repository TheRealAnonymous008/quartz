* A message-passing algorithm for performing inference on a [[Probabilistic Graphical Models|graphical model]]. 


* Let $X_1,\dots, X_n$ be [[Random Variables and Probability Distributions|random variables]] with a joint probability function $p$. The task is to compute the marginal distributions. 
  
  Define a factor graph with variables $V$ and factors $F$. 
* Let $v$ be a variable node and $a$ a factor node connected to $v$ in the factor graph. Let $f_a$ be the factor corresponding to $a$. 
	* A **message** in this case is a re-usable partial sum that can be used in computing the marginal probability
	* A message $\mu_{v\to a} : \text{Dom}(v) \to \mathbb{R}$  is defined as follows
	  $$
	  \mu_{v\to a}(x_v) = \prod_{a^\ast \in N(v)-\set{a}} \mu_{a^\ast \to v}(x_v)
	  $$
	  Where $N(v)$ is the set of neighboring factor nodes. 
	  If $N(v)-\set{a}$ is empty, we use the [[Probability Distributions Zoo|uniform probability distribution]].

	* A message $\mu_{a\to v}:\text{Dom}(v)\to \mathbb{R}$  is defined as follows
	  $$
	  \mu_{a\to v}(x_v) = \sum_{x_a':x_v'=x_v} \left( f_a(x_a') \prod_{v^\ast \in N(a)-\set{v}} \mu_{v^\ast\to a} (x_{v^\ast}')\right)
	  $$
	  Where $N(a)$ is the set of neighboring variable nodes of $a$. If $N(a)-\set{v}$ is empty, we have $\mu_{a\to v}(x_v)=f_a(x_v)$. 

* The marginal probabilities can be approximated as follows
  $$
  \begin{split}
  p_{X_v}(x_v) &\propto \prod_{a\in N(v)} \mu_{a\to v} (x_v)  \\
  p_{X_a} (x_a) &\propto f_a(x_a) \prod_{v\in N(a)} \mu_{v\to a}(x_v)
  \end{split}
  $$

* A [[Bayesian Statistics#Maximum A Posteriori|Maximum A posteriori]] estimate can be obtained for $\mu_{a\to v}(x_v)$ by doing an argmax instead of a sum.
  
  $$
  \mu_{a\to v}(x_v) = \underset{x_a':x_v'=x_v}{\mathrm{argmax}} \left( f_a(x_a') \prod_{v^\ast \in N(a)-\set{v}} \mu_{v^\ast\to a} (x_{v^\ast}')\right)
  $$

* The Belief Propagation algorithm gives an exact value if the PGM is [[Tree|acyclic]].
  
  However, it can still be performed for graphs with cycles with no exact value guarantees. 

* The update rule for BP can be modified as long as the set of fixed points remains the same.
* For notational brevity, let $m^k$ denote the message to be passed at the $k$-th step. Then with a **damped** update rule
  $$
  \overline{m}^k = \alpha m^k + (1-\alpha)m^{k-1}
  $$


# Links
* [[Information Theory]]