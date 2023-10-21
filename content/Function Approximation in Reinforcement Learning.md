* *Rationale*: We often have memory constraints that do not allow us to explore large state spaces. Hence we sample from a small state space.
	* However, we need a way to make decisions on unsampled states using those that we have sampled. This is done via **function approximation
	* This is, in fact, [[Supervised Learning]]. It makes changes generalizable but controlling them more complex.
		* *It should be noted, that we must make use of models that can handle non-stationarity.*
		* Nonstationarity comes in either because the environment is non-stationary or because of [[Dynamic Programming for Reinforcement Learning|bootstrapping]] which makes our estimates change.
	* It also make RL extensible to **partially observable problems** where states are not fully visible to the agent.
	* It cannot augment states with memories of past observations.
# Prediction
* Estimates and Update rules in Reinforcement learning can be formulated with the following formula (analogous to gradient descent): 
  $$\text{New} = \text{Old} + \text{Step} \left[ \text{Target} - \text{Old} \right]$$
  We notate this with $\text{OLD}\mapsto \text{NEW}$ 

* We represent the value function as a parameterized functional form with weight vector $w\in \mathbb{R}^d$. We denote 
  $$\hat{v}(s,w)\approx v_\pi(s)$$
   for the approximate function of state $s$ with weight vector $w$.
	* Note, *assume we have more states than weights*. This assumption is founded on the fact *we have more states than actions*.
* We specify a **state distribution** which specifies how much we care about errors in value estimates for state $s$. We denote this with $\mu(s)$. 
	* We require this state distribution because state updates can affect other states. 
	* Making one state accurate makes the estimations for other states inaccurate.
	* We often choose $\mu(s)$ to be the fraction of time spent on $s$.


# Topics
* [[On Policy Prediction and Control with Approximation ]]
# Links
* [[Reinforcement Learning]]