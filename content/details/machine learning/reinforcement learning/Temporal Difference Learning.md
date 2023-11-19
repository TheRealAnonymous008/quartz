* Temporal Difference (TD) learning is a combination of Dynamic Programming (via bootstrapping) and Monte Carlo Methods (via learning from experience).
* *The central idea is to learn while in the middle of the episode using an appropriate estimate based on the agent's current predictions*. 
# Advantages
* Unlike DP, it does not require a model of the environment.
* Unlike Monte Carlo, it does not require simulating the whole episode.
	* This means that small changes in the configuration of the environment (i.e., start states) do not require us to simulate multiple episodes. Instead, we can simply transfer knowledge from one model to another.
	* It also makes it applicable to continual tasks, which Monte Carlo cannot do.
* Compared to Monte Carlo, it learns much faster because it does not discount or ignore episodes.
* Compared to batch Monte Carlo, batch TD tends to *converge towards a model that would likely be correct for future data* rather than on a model that is correct only for the present data.
	* Specifically, TD converges towards the [[Bayesian Models|Maximum Likelihood]] via the **certainty equivalence estimate** -- which is equivalent to assuming that the estimate of the underlying process was known with certainty rather than being approximated.
# TD Prediction
* TD methods *wait until the next time step* until they reward a target and make a useful update using $R_t$. The update takes the form 
  $$
  V(S_t)\gets V(S_t) +\alpha [R_{t+1} +\gamma V(S_{t+1}) - V(S_t)]
  $$

## TD-errors
* The target for updating is $R_\Sigma$ (i.e., the estimated discounted value when the agent takes $n$ steps from the current state).
	* $R_\Sigma$ is the **target estimate**. In TD-0 this is given as 
	  $$
	  R_{\Sigma}=R_{t+1}+\gamma V(S_{t+1})
	  $$
	  
	* It makes use of two estimates -- the sampled reward $R_{t+1}$, and the estimated value $V(S_{t+1})$. The sampled estimate makes use of only the successor state's reward rather than the full distribution of successors.
	* The error in this estimate is proportional to the **temporal differences** between predictions.
	* The **TD-error** is defined as
	  $$
	  \delta_t=R_{t+1}+\gamma V(S_{t+1}) - V(S_t)
	  $$
	  
* The [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]] error can be written as a sum of discounted TD errors 
  $$
  G_t-V(S_t)=\sum_{k=t}^{T-1}\gamma^{k-1}\delta _k
  $$
  
	* This identity is not exact if $V$ is updated during the episode, but if the step size is small then it may still hold approximately.

* In an [[A Unified View on Reinforcement Learning Approaches#Average Reward Formulation|average reward context]] we have the TD-errors as 
  
  $$
  \begin{split}
  \delta_t&=R_{t+1}-r(\pi) + V(S_{t+1}) - V(S_t) \\
  &= R_{t+1} -r(\pi) +Q(S_{t+1}, A_{t+1}) - Q(S_t,A_t)
  \end{split}
  $$
  
* Note we can replace everything in the TD-error formulae with estimates. 
# TD Control
### SARSA
* Stands for $(S_t, A_t, R_{t+1}, S_{t+1}, A_{t+1})$. 
* It is an on-policy control method. Hence, it uses an $\epsilon$-greedy policy for exploration (see [[Monte Carlo Methods in Reinforcement Learning#Optimization and Relaxation|here]]).
* We estimate the action-value function for a given policy by considering transitions from state-action to state-action pair using the following update rule: 
  $$
  Q(S_t,A_t) \gets Q(S_t,A_t)+ \alpha \left[R_{t+1} +\gamma Q(S_{t+1}, A_{t+1})-Q(S_t, A_t)\right]
  $$
  
* We then choose actions based on $Q$ optimally. *Note: this is important*. If a suboptimal policy were enacted, the quality will degrade. 
* *SARSA learns the bad policies during the episode and can quickly adjust*.
* It can only perform well in the long run with a small step size $\alpha$, at which short term performance is poor.
### Q-Learning
* An off-policy TD control algorithm. It is off-policy because we use a policy derived from $Q$ (which lets us move to $S_{t+1}$ in order to update the optimal policy with respect to the current state, action pair $S_t, A_t$.  
* It is characterized by updating 
  $$
  Q(S_t,A_t)\gets Q(S_t,A_t)+\alpha\left[R_{t+1}+\gamma \max_aQ(S_{t+1},a) - Q(S_t,A_t)\right]
  $$
  
* *Actually learns the values of the optimal policy, but it is not good for online learning.*
### Expected SARSA
* An off policy generalization of Q-learning and SARSA.
* The target is
  $$
  G_{t:t+1}=R_{t+1}+\gamma\sum_a\pi(a\mid S_{t+1}) Q_t(S_{t+1},a)
  $$
  
* Moves towards the expected value, taking into account how likely each action is under the current policy. That is, the rule becomes
  $$
  \begin{split}Q(S_t,A_t)&\gets Q(S_t,A_t)+\alpha[R_{t+1} +\gamma \mathbb{E}_\pi \left[Q(S_{t+1}, A_{t+1}) \mid S_{t+1} ] - Q(S_t,A_t)\right]  \\ &= Q(S_t, A_t) + \alpha\left[R_{t+1} +\gamma \left[\sum_{a} \pi(a\mid S_{t+1} ) \ Q(S_{t+1}, a)\right] - Q(S_t,A_t)\right] \end{split}
  $$
  
* More computationally complex than SARSA, but *eliminates variance due to random selection* of $A_{t+1}$. 
### Double Learning
* **Maximization bias** - a bias that results from implicitly assuming a maximum over estimated values, as in the other TD methods. The bias arises because the maximum is always above the expected (or even actual) value of the estimate, and *we always use the same samples both to determine maximizing action and to estimate its value.*
* **Double Learning** means to divide the plays in two sets and use them to learn two independent estimates $Q_1(a)$ and $Q_2(a)$ as an estimate of the true value $q(a)$.  
	* $Q_1$ will be used to determine the maximizing action $A^\ast = \underset{a}{\text{argmax}} Q_1(a)$ 
	* $Q_2$ will provide the value estimate via
	  $$
	  Q_2(A^\ast)=Q_2\left(\underset{a}{\text{argmax}}  \ Q_1(a)\right)
	  $$
	  
	* A second unbiased estimate is also derivable as follows
	  $$
	  Q_1(A^\ast)=Q_1\left(\underset{a}{\text{argmax}} \ Q_2(a)\right)
	  $$
	  
	* The actual process of updating involves dividing the time steps in two such that in each, we either update $Q_1$ or $Q_2$ using the formulate above.

* **Double Q Learning** makes use of the following update rule 
  $$
  \begin{split}
  A^\ast_{t+1} &= \underset{a}{\text{argmax}}  \ Q_1(S_{t+1}, a)  \\ 
  
  Q_1(S_t,A_t) &\gets Q_1(S_t,A_t) + \alpha \left[ R_{t+1} + \gamma Q_2 (S_{t+1}, A_{t+1}^\ast)  - Q_1(S_t,A_t)\right]
  
  \end{split}
  $$
  Where we alternate between using this and swapping the roles of $Q_1$ and $Q_2$. 
* We may also base the policy on the average or sum of $Q_1$ and $Q_2$.

### Retrace 
* Retrace [^Munos_2016] is an off-policy Q-value estimation algorithm with guaranteed convergence. 
* It addresses how importance weights on their own can introduce high variance 
* The estimation involves using **truncated importance weights**, which means that the importance weights should be no more than $c$. 
  
  This means that to improve the estimate $Q(S_t,A_t)$ we increment by 
  
  $$
  \gamma^t \min (c, \rho_t) \delta_t
  $$

[^Munos_2016]: Munos et al. (2016) [Safe and efficient off-policy reinforcement learning](https://proceedings.neurips.cc/paper_files/paper/2016/file/c3992e9a68c5ae12bd18488bc579b30d-Paper.pdf) 

# Links
* [[Dynamic Programming for Reinforcement Learning]] - for more on Dynamic Programming in RL
* [[Monte Carlo Methods in Reinforcement Learning]] - for  more on Monte Carlo in RL
* [[N-step Bootstrapping]] - a generalization of TD-learning

* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 6-7,10]]
	* 6.4 - SARSA
	* 6.5 - Q learning
	* 6.6 - Expected SARSA
	* 6.7 - Double Learning
	* 7.2 - n-step SARSA
	* 7.4 - Control Variates
	* 7.5 - Tree Backup
	* 7.6 - $Q(\sigma)$. 
	* 10.3 - Average reward TD error.
* [Q-Learning: Model Free Reinforcement Learning and Temporal Difference Learning](https://www.youtube.com/watch?v=0iqz4tcKN58) - supplementary material for Q-learning

