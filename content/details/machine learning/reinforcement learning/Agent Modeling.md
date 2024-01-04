* **Agent modeling** is the task of learning explicit models of other agents to predict their own actions based on their past chosen actions 
* *Rationale*: Agents may take off-equilibrium actions for which the policy suggested in something like [[Joint Action Learning]] would not prescribe any action.

* **Policy Reconstruction** - the goal is to learn models $\hat{\pi}_j$ of the policies $\pi_j$ of the other agents. 
	* This can be framed as a [[Supervised Learning]] problem with the past observed state-action pairs of the modelled agent as input and the output being a new action $a$. 
	* The agent then selects a best response policy using these models 
	  $$
	  \pi_i \in \text{BR}_i (\hat{pi}_{-i})
	  $$

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
  \text{AV}_i(s,a_i) = \sum_{a_{-i}\in A} Q_i(s, \braket{a_i,a_{-i}}) \ \prod_{j\ne i} \hat{\pi_j}(a_j\mid s)
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

# Links 
* [[MARL Problem Statement]]
* [[MARL from a Game Theoretic Perspective]]

* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] - Ch 6.3