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
  \begin{split}Q(S_t,A_t)&\gets Q(S_t,A_t)+\alpha[R_{t+1} +\gamma E_\pi \left[Q(S_{t+1}, A_{t+1}) \mid S_{t+1} ] - Q(S_t,A_t)\right]  \\ &= Q(S_t, A_t) + \alpha\left[R_{t+1} +\gamma \left[\sum_{a} \pi(a\mid S_{t+1} ) \ Q(S_{t+1}, a)\right] - Q(S_t,A_t)\right] \end{split}
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

# N-Step Bootstrapping
* These methods act as intermediates in the spectrum between Monte Carlo (update at the end of the episode) and TD(0) (update immediately after),
* **$n$-step TD methods** are those that update based on the temporal difference over $n$ steps.
### Prediction
* The return for an $n$-step update is defined as
  $$
  G_{t:t+n}=R_{t+1}+\gamma R_{t+2}
  +\dots+\gamma^{n-1}R_{t+n}+\gamma^n V_{t+n-1}(S_{t+n})
  $$
  For all $n\ge 1$ and $0\le t < T-n$ 
* The n-step return is an *approximation to the true return by truncating it after $n$ steps*.
* We learn the state updates by using the following (simply substitute the n-step return for the formula in [[#TD Prediction]]
  $$
  V_{t+n}(S_t)=V_{t+n-1}(S_t)+\alpha\left[ G_{t:t+n} -V_{t+n-1}(S_t)\right]
  $$
  
* To compensate for the fact we do not perform updates at the first $n-1$ steps in the beginning, we make the updates at the end of the episode after termination and before starting the next episode.
* Like Monte Carlo, the n-step return can be *written as a sum of TD errors*.  
  $$
  G_{t:t+n}-V_{t+n}(S_t)=\sum_{k=t}^{t+n-1}\gamma^{k-1}\delta _k
  $$
  
[^1]
* **The Error Reduction Property** of $n$-step returns means that the worst error of the expectation of an $n$-step return is guaranteed to be a better estimate of $v_\pi$ than $V_{t+n-1}$ is. 
  $$
  \max_s\left|E_\pi \left[ G_{t:t+n} \mid S_t=s\right] - v_\pi(s)\right| \le \gamma^n \max_s \left|V_{t+n-1}(s)-v_\pi (s)\right|
  $$
  
	* This implies convergence to correct predictions as our n-step returns get progressively closer to the true value.

[^1]: Deriving this is a straightforward substitution, assuming the value function doesn't change.

### n-step SARSA
* A generalization of SARSA. 
* It still makes uses of sample transitions.
* We simply redefine the $n$-step return to make use of $Q$. 
  $$
  G_{t:t+n}=R_{t+1}+\gamma R_{t+2} +\dots +\gamma^{n-1}R_{t+n}+\gamma^n Q_{t+n-1}(S_{t+n},A_{t+n})
  $$
  And $G_{t:t+n}=G_t$ if $t+n\ge T$. 

* The update rule becomes 
  $$
  Q_{t+n}(S_t,A_t)=Q_{t+n-1}(S_t,A_t) + \alpha\left[G_{t:t+n} -Q_{t+n-1}(S_t,A_t)\right]
  $$
  
* The value of other states remain unchanged. That is $Q_{t+n}(s,a)=Q_{t+n-1}(s,a)$ for all $s,a$ such that $s\ne S_t, a\ne A_t$. 

### n-step Expected SARSA
* It makes use o sample transitions, except for the last state which is fully branched.
* Extends $n$-step SARSA as follows. We redefine the $n$-step return as 
  $$
  G_{t:t+n}=R_{t+1}+\gamma R_{t+2} +\dots +\gamma^{n-1}R_{t+n}+\gamma^n \hat{V}_{t+n-1}(S_{t+n})
  $$
  And $G_{t:t+n}=G_t$ if $t+n\ge T$. 
* We call $\hat{V}$ the **expected approximate value** which is defined as 
  $$
  \hat{V}_t(s)=\sum_{a}\pi(a\mid s)Q_t(s,a)
  $$
  
* If $s$ is a terminal state, then the expected approximate value is defined as $0$.

### $n$-step Off-Policy Learning
* We make use of the [[Importance Sampling#N-step Returns|importance sampling ratio for n-step returns]] $\rho$.
* The update rule then becomes weighted with $\rho$ as follows 
  $$
  V_{t+n}(S_t)=V_{t+n-1}(S_t)+\alpha \rho_{t:t+n-1}\left[ G_{t:t+n} -V_{t+n-1}(S_t)\right]
  $$
  
* For using the Q function we use $\rho_{t+1:t+n}$ since we update on state-action pairs. 
* For expected SARSA, we use $\rho_{t+1 : t+n-1}$. All possible actions are taken into account in the last state; the one actually taken has no effect and does not have to be corrected for.

* *The drawback with off-policy methods is shown here -- it requires slower training since it has higher variance updates*.

### Control Variates
* *One problem with importance sampling is high variance, especially when actions may not be taken*
* We modify the definition of the return in this case to make use of an *off-policy definition*
  $$
  G_{t:h}=\rho_t(R_{t+1}+\gamma_{t+1:h}) + (1-\rho_t)V_{h-1}(S_t)
  $$
  and where $G_{h:h}=V_{h-1}(S_h)$. 
	* Here we remove the problem of high variance by having the target equal the estimate (i.e., do not change when $\rho_t=0$).
* For action values, we apply importance sampling to actions except the first.
	* *Rationale*: The first action is being evaluated and has already been taken, so the reward must be learnt in full.
	* The formula becomes 
	  $$
	  G_{t:h}=R_{t+1}+ \gamma \rho_{t+1} \left( G_{t+1:h} -Q_{h-1}(S_{t+1},A_{t+1})\right)+\gamma\hat{V}_{h-1}(S_{t+1})
	  $$
	  
	* If $h<T$, we have $G_{h,h}=Q_{h-1}(S_h,A_h$)
	* Otherwise, $G_{T-1:h}=R_T$.

### Tree Backup Algorithm
* It makes use of all state transitions fully branched without sampling.
* In Tree-backup, *updates are performed from the leaves of the tree. The actual actions taken do not participate*.
* Each leaf contributes to the target with a weight proportional to its probability of occurring under target policy $\pi$.
* Actions taken contribute to the probability of the leaves in the next level down.
* At the last node of the tree backup diagram, we consider all actions as untaken.

* We use the same one step return target $G_{t:t+1}$ as [[#Expected SARSA]]. This form is generalized as follows 
  $$
  G_{t:t+n}=R_{t+1}+\gamma\sum_{a\ne A_{t+1}} \pi(a\mid S_{t+1} ) \ Q_{t+n-1}(S_{t+1}, a) + \gamma\pi(A_{t+1}\mid S_{t+1}) G_{t+1:t+n}
  $$
  For $t<T-1$, $n\ge 2$. 
* A special case: $G_{T-1:t+n}=R_T$.

* The target is then used for the usual action-value update from [[#n-step SARSA]].

### n-Step $Q(\sigma)$
* Unifies [[#n-step SARSA]], [[#Expected SARSA]], and [[#Tree Backup Algorithm]] by providing  a choice. Either we fully branch or take samples based on some probability $\sigma_t$ at time step $t$.
	* If we fully branch all the time we get Tree Backup.
	* If we take samples, all the time we get SARSA.
	* If we take samples except for the last state we get Expected SARSA.
* $\sigma_t$ may be a function on a state, action, or state-action pair at $t$
* We use $\sigma_t$ as an interpolator. The return is now defined as 
  $$
  G_{t:h}=R_{t+1} + \gamma\left(\sigma_{t+1}\rho_{t+1} + (1-\sigma_{t+1})\pi(A_{t+1}\mid S_{t+1})\right) \left(G_{t+1:h} -Q_{h-1} (S_{t+1},A_{t+1})\right) + \gamma \hat{V}_{h-1}(S_{t+1})
  $$
  
  For $t<h<T$.
  
  If $h<T$, we end with $G_{t:h}=Q_{h-1}(S_h,A_h)$. 
  
  If $h=T$, we end with $G_{T-1:T} = R_T$.

* We then perform the update defined in [[#n-step SARSA]] except without importance sampling ratios. 

# Links
* [[Dynamic Programming for Reinforcement Learning]] - for more on Dynamic Programming in RL
* [[Monte Carlo Methods in Reinforcement Learning]] - for  more on Monte Carlo in RL

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
