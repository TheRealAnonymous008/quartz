* **Agent modeling** is the task of learning explicit models of other agents to predict their own actions based on their past chosen actions 
* *Rationale*: Agents may take off-equilibrium actions for which the policy suggested in something like [[Joint Action Learning]] would not prescribe any action.

* **Policy Reconstruction** - the goal is to learn models $\hat{\pi}_j$ of the policies $\pi_j$ of the other agents. 
	* This can be framed as a [[Supervised Learning]] problem with the past observed state-action pairs of the modelled agent as input and the output being a new action $a$. 
	* The agent then selects a best response policy using these models 
	  $$
	  \pi_i \in \text{BR}_i (\hat{pi}_{-i})
	  $$

# Classic Approaches 
## Fictitious Play 
* In **fictitious play** each agent models the policy of other agents as a stationary [[Random Variables and Probability Distributions|probability distribution]] $\hat{\pi}_j$ estimated from the empirical distribution of agent $j$'s past actions. 
* It is defined for [[Dynamic Games of Incomplete Information|non-repeated games]]
* More formally if $C(a_j)$ be the number of times $a_j$ was selected by agent $j$, then 
  
  $$
  \hat{\pi}_j(a_j) = \frac{C(a_j)}{\sum_{a_j'}{C(a_j')}}
  $$
  For convenience, we may assume that the initial distribution is a uniform distribution. 

* In each episode, the best response action is chosen given by 
  
  $$
  \text{BR}_i(\hat{\pi}_{-i}) = \underset{a_i\in A_i}{\text{argmax}} \ \sum_{a_{-i}\in A_{-i}} R_i(\braket{a_i,a_{-i}}) \ \prod_{j\ne i} \ \hat{\pi}_j (a_j )
  $$
* *Fictitious play gives optimal actions; it cannot give a stochastic policy*. However, fictitious play can converge to random equilibria. 
	* If the agents' actions converge, then the converged actions form a Nash equilibrium 
	* If in any episode the agents’ actions form a Nash equilibrium, then they will remain in the equilibrium in all subsequent episodes.
	* If the empirical distribution of each agent’s actions converges, then the distributions converge to a Nash equilibrium of the game.
	* The empirical distributions converge in several game classes, including in two-agent zero-sum games with finite action sets
	* For games done repeatedly, the agent will only consider the current interaction 
	* For [[Dynamic Games of Complete Information#Repeated Games|repeated games]], the action may depend on past history

## JAL-AM 
* Combines Joint-Action Learning with Agent Modeling 
*  Here agents learn empirical distributions based on past actions and conditioned on the state 
  $$
  \hat{\pi_j} (a_j\mid s) = \frac{C(s,a_j)}{\sum_{a_j'} (s,a_j')}  
  $$

* $\text{AV}$ denotes the expected return to agent $i$ for taking action $a$. [^jalam_1]
  
  $$
  \text{AV}_i(s,a_i) = \sum_{a_{-i}\in A_{-i}} Q_i(s, \braket{a_i,a_{-i}}) \ \prod_{j\ne i} \hat{\pi_j}(a_j\mid s)
  $$

![[JAL-AM.png]]
<figcaption> JAL-AM. Image taken from Albrecht, Christianos and Schafer </figcaption>

[^jalam_1]: This is essentially the best response action except using $R=Q$ instead. 

* Like AM, it returns best response actions. 
* *JAL-AM does not require observing the rewards of other agents*. 

## Bayesian Learning 
* Extends [[#Fictitious Play]] and [[#JAL-AM]] by incorporating uncertainty and considering a distribution of models rather than a single model. The choice of models is governed by [[Bayesian Statistics|beliefs]]. 
* *The goal is to maximize over beliefs, and in particular, compute the best-response action that maximize the value of information*.
* The **value of information** evaluates how the outcomes of an action may influence the agent's belief. 
	* *Rationale*: Some actions may reveal more information about the policies of other agents than others .We are effectively using [[Dynamic Games of Incomplete Information|the framework described here]].

* Let $\hat{\Pi}_j$ be the space of possible agent models for agent $j$ and where each model $\hat{\pi}_j$ chooses based on the interaction history $h$. 
  
  After observing agent $j$'s action $a_j^t$ in state $s^t$, we update using a Bayesian posterior distribution (shown below is the numerator but it needs to be normalized afterward)
  
  $$
  P(\hat{\pi}_j \mid h^{t+1})  \propto \hat{\pi}_j (a_j^t\mid h^t) \ P(\hat{\pi}_j \mid h^t) 
  $$
  

* The value of information is then calculated using the following  [^bayes_1]
  
  $$
  \begin{split}
  \text{VI}_i(a_i\mid h) &= \sum_{\hat{\pi_{-i}} \in \hat{\Pi}_{-i}} \ P(\hat{\pi}_{-i} \mid h)  \sum_{a_{-i} \in A_{-i}} Q_i (h, \braket{a_i,a_{-i}})  \ \prod_{j\ne i} \hat{\pi_j (a_j\mid h)} \\
  
  Q_i(h,a) &= \sum_{s'\in S} \mathcal{T} (s'\mid s(h), a) \ \bigg[ R_i(s(h), a, s') + \gamma \max_{a_i'\in A_i} \text{VI}_i (a_i \mid \braket{h,a,s'}\bigg]
  \end{split}
  $$
[^bayes_1]: In effect, value of information is an extension of the regular state-based value function $V$

* The agent then selects the action 
  $$
  a_i \in \underset{a_i}{\text{argmax}} \ \text{VI}_i(a_i\mid h^t)
  $$

# DNN-based Approaches 
* *The goal is to learn generalizable models of the policies of other networks using deep neural nets.* 
* This is applicable especially when we have decentralized execution and  where agents only have access to local observation history.

## JAL with Deep Agent Models 
* Extends [[#JAL-AM]]. Here, each agent's model is a [[Neural Network]] $\hat{\pi}^i_{-i}=\{\hat{\pi}_j^i\}_{j\ne i}$ 
* The agent model is learnt using the past actions of the other agents and the observation history. This is encapsulated in the following loss function 
  
  $$
  \mathcal{L} (\phi_j^i) = -\log \hat{\pi}_j^i (a_j^t \mid h_i^t \\ ; \phi_{j}^I)
  $$
* We define the action value as follows. An approximation to make it more tractable is also given using a sample of $K$ joint actions from the models of all other agents. 
  $$
  \begin{split}
  \text{AV}(h_i,a_i;\theta_i) &= \sum_{a_{-i}\in A_{-i}} Q(h_i, \braket{a_i,a_{-i}} ; \theta_i) \ \prod_{j\ne i} \hat{\pi}_j^i(a_j\mid h_i; \theta_j^i ) \\ 
  &\approx \frac{1}{K} \sum_{k=1}^K Q(h_i,\braket{a_i,a_{-i}^k} ; \theta_i) \bigg\vert_{a_j^k\sim \hat{\pi}_j^i (\cdot \mid h_i)}
  \end{split}
  $$

* Each agent also trains a centralized action value $Q$ parameterized by $\theta_i$ using DQN with the loss function of 
  $$
  \begin{split}
  \mathcal{L} (\theta_i) &= \frac{1}{|\mathcal{B}|} \sum_{(h_i^t, a^t,r_i^t, h_i^{t+1})\in\mathcal{B}} \bigg(r_i^t +\gamma\max_{a_i'\in A_i} \text{AV}(h_i^{t+1}, a_i';\overline{\theta}_i)  - Q(h_i^t ,\braket{a_i^t, a_{-i}^t}; \theta_i)\bigg)^2
  \end{split}
  $$


![[Deep JAL.png]]<figcaption> Deep JAL. Image taken from Albrecht, Christianos and Schafer </figcaption>

* Using the sampling approximation for $\text{AV}$ may lead to higher variance but also higher exploration with potentially faster convergence. 

## Policy Reconstruction
* *Rationale*: It may not be feasible to use the policies and value functions of the other agents, even with using a model. This is because 
	* We may be running on decentralized execution 
	* The policies of the agents may be too complex. 
	* The policies of the agents change during learning. 

* One common approach is to use [[Encoder-Decoder Network]]. We may also use [[Transformer Model|transformers]]. We have two networks 
	* The encoder $f^e$  gives a representation $m_i^t=f^e(h_i^t; \psi_i^e)$
	* The decoder gives action probabilities $\pi_{-i}^{i,t}=f^d(m_i^t;\psi_i^d)$

* The encoder-decoder networks are jointly trained using cross-entropy loss. 
  
  $$
  \mathcal{L}(\psi_i^e, \psi_i^d) = \sum_{j\ne i} -\log \hat{\pi}_j^{i,t} (a_j^t)
  $$

* Other approaches such as those [[MARL Deep Learning|here]] can be augmented by conditioning on the learnt representation $m_i^t$.

## Extensions 
* **Recursive Reasoning** - an extension of agent modeling where agents consider how other agents might react to their decision making, or how their actions might affect the learning of other agents 
* **Opponent Shaping** - an extension where agents try to shape their opponents -- leveraging the fact that other agents are learning and exploiting this objective. 

# Research 
* [^Weiner_2016] develops a method to determine the intentions of other agents in the environment and determines whether or not to cooperate or compete, leading to the *emergence of social norms*.
	* The paper aims to bridge high-level strategic decision making over abstract social goals such as cooperation and competition with low-level planning over realizing these goals.. This is done through **hierarchical social planning** where *learning is done on both levels*
	* *Low-level learning has two modes -- cooperative and competitive High-level learning decides whether to cooperate or compete*. 
	* *Cooperation is achieved through a group utility function*
		* A high level policy will be conditioned on the joint actions. Low level policies of each agent marginalize out the actions of the other player from the joint policy. 
		* Policies contain intertwined intentions. *Cooperation is built as part of planning*. 
		* Agents interact and after each interaction infer how much they weigh the utility of the other agent. *This is akin to a form of [[Dynamic Games of Complete Information|virtual bargaining]]* 
	* *Competition is achieved through maximizing individual utility*
		* A hierarchy is established with level-$K$ agents best responding to level-$(K-1)$ agents. Level $0$ agents do not consider the existence of other players. 
		* Two mechanisms are implemented -- a model-based approach which is standard agent modeling, and a model-free approach for maximizing the agent's own goals 
	* For higher level strategic learning, planning considers player's intentions to cooperate or compete.

	[^Weiner_2016]: Weiner et al. (2016) [Coordinate to cooperate or compete: Abstract goals and joint intentions in social interaction](https://par.nsf.gov/servlets/purl/10026426)
# Links 
* [[MARL Problem Statement]]
* [[MARL from a Game Theoretic Perspective]]

* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] - Ch 6.3, 9.6