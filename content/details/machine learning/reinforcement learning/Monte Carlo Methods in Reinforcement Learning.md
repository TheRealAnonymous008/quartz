# Overview
* In the context of reinforcement learning, Monte Carlo Methods are those that *require no prior knowledge* about the environment, and where the agent *learns from experience*. The agent can also simply learn the values of a *sample of the state space*.
* It is based on *averaging sample returns*. On each state, simulate episodes starting from that state and average the returns from each state. 
* *Each estimate from each state is treated independent*. The estimate from one state does not depend on the estimate from subsequent states. 
* The problem framed this way is analogous to having many interrelated [[The Exploitation-Exploration Trade-Off|bandit problems]] with a non-stationary distribution (since everything is learnt).
* **Batching** pertains to processing multiple episodes before performing a single update. This is also applicable for [[Temporal Difference Learning]]. 

### Advantages and Disadvantages
* Monte Carlo methods find optimal policies given only sample episodes and *no other knowledge of the environment's [[Markov Processes in Machine Learning|dynamics]]* unlike [[Dynamic Programming for Reinforcement Learning|DP]]. 
* Because it does not perform bootstrapping, *Monte Carlo is not susceptible to violations of the Markov Property*.
* It can operate only on a *sample of states*, and thus does not require estimating the value of all states in the state space.

* One disadvantage is that *it has to simulate the entire episode* which may not be applicable in continuous tasks or long tasks.
	* It posits that an optimal action could have been taken anywhere in the episode.
* Another disadvantage is that *Monte Carlo tends to overfit the data* by converging to a model of the environment that minimizes the error seen in the training data.
* Compared to [[Temporal Difference Learning]], Monte Carlo follows [[Frequentist Statistics]] hence it is only better on existing data but not future data.

### Estimating Action Values
* Let $\pi$ be a policy and 
  
  $q_{\pi}(s,a)$ be an estimator of the value of action $a$ at state $s$. 
  
  We say $(s,a)$ is **visited** if during an episode, it has been encountered.
	* In **every visit Monte-Carlo**, estimate $q_{\pi}(s,a)$ as the average of the returns that have followed all the visits to $(s,a)$, counting all states. 
	* In **first-visit Monte Carlo**, estimate $q_{\pi}(s,a)$ as the average of the returns but only after $(s,a)$ has been visited for the first time.

* Let $\mathcal{T}(s)$ denote the time steps of interest. 
	* For first visit, this would be every time step where the state was visited first in its episode.
	* For every visit, this would be all time steps where the state is visited.

* Both First Visit and Every Visit Monte Carlo converge to the true value function $v_\pi$ as $t=\infty$ samples are chosen.
* The [[Backups in Reinforcement Learning|backup]] for a Monte Carlo approach is just a straight path which follows the trajectory of an episode.

* In a Monte Carlo approach, *it is better to use the action values* since state values are insufficient for determining the policy when the model is unknown. 

* Some state-action pairs may not be explored as much so we must *maintain exploration*. 
	* One way is through the assumption of **exploring starts** where episodes start on a state-action pair and every pair has a nonzero probability of being selected at the start.
	* Another is by having a stochastic policy that can select any state-action pair with nonzero probability. That way *eventually all state-action pairs are considered*.
# Monte Carlo Control
* Similar to [[Dynamic Programming for Reinforcement Learning|Dynamic Programming]], the Monte Carlo process involves cycling between policy evaluation and improvement using approximate value functions and policies.
	* **Evaluation** is done by estimating the action values of the given policy.
		* Although action-value estimation is done with multiple episodes, implementations alternate the evaluation with improvement on an episode-by-episode basis.
	* **Improvement** is done by greedily selecting the best action with respect to the current value function. That is, selecting
	  $$
	  \pi(s)=\underset{a}{\text{argmax}} \ q(s,a)
	  $$
	  

* By the Policy Improvement Theorem (see [[Dynamic Programming for Reinforcement Learning|here]]), the Monte Carlo approach converges to the optimal policy and value function.

### Optimization and Relaxation
* To be amenable to computation, we should relax the assumption of requiring an infinite number of episodes.
	* This can be done by either setting a *bound on the improvement of the $q$ estimate* and terminating evaluation when this is sufficiently small. The problem is this may still require many episodes for true convergence
	* An alternative is *to run evaluation for one iteration, for one episode*. Here, the flow goes -- run episode, evaluate once , improve once, repeat.
		* *Convergence of this approach to the optimal policy is an open problem*.

* Additionally ,we may need to remove the assumption of exploring starts since there are possibly many state action pairs.
	* One way is through **on-policy** methods where we improve the policy for decision making.
		* The idea of this approach is to still make use of GPI, however we change the policy to be $\epsilon$-greedy rather than greedy on $q(s,a)$.
		* Convergence is assured via the Policy Improvement Theorem.
		* The existence of an optimal policy is guaranteed by the fact that the following policies have equivalent value functions:
			* The $\epsilon$-greedy policy found through Monte Carlo policy iteration
			* The regular greedy policy found through GPI, but where the environment is modified to "randomize" the actions of the policy chosen with $\epsilon$ probability. [^1]

[^1]: See more at [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 5.4]]
# Off-Policy Methods
* See [[A Unified View on Planning and Learning|here]] for more on off-policy. Note that we make use of [[Importance Sampling]] 

* Ordinary and Weighted importance sampling for First-Visit MC are subject to [[Statistical Estimators#Bias-Variance Tradeoff|bias variance tradeoff]]. Ordinary has low bias, high variance (often infinite) Weighted has high bias, low variance (though the bias converges to $0$).
* For Every-Visit MC, both ordinary and weighted importance sampling  are biased but this bias converges [[Asymptotic Analysis|asymptotically]] to $0$.

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 5]] 
	* 5.3 - more on Monte Carlo with Exploring Starts.
	* 5.4 - the mathematical formulation of Monte Carlo without Exploring Starts.
	* 5.6 - an incremental implementation of off-policy Monte Carlo using importance sampling.
	* 5.7 - an implementation of off-policy Monte Carlo.
