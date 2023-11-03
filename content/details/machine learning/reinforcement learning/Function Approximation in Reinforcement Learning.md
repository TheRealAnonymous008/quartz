* *Rationale*: We often have memory constraints that do not allow us to explore large state spaces. Hence we sample from a small state space.
	* However, we need a way to make decisions on unsampled states using those that we have sampled. This is done via **function approximation**
	* This is, in fact, [[Supervised Learning]]. It makes changes generalizable but controlling them more complex.
		* *It should be noted, that we must make use of models that can handle non-stationarity.*
		* Nonstationarity comes in either because the environment is non-stationary or because of [[Dynamic Programming for Reinforcement Learning|bootstrapping]] which makes our estimates change.
	* It also make RL extensible to **partially observable problems** where states are not fully visible to the agent.
	* It cannot augment states with memories of past observations.

* A tradeoff with functional approximation is we can no longer use the policy improvement theorem.
# Prediction
* We represent the value function as a parameterized functional form with weight vector $w\in \mathbb{R}^d$. We denote 
  $$
  \hat{v}(s,w)\approx v_\pi(s)
  $$
   for the approximate function of state $s$ with weight vector $w$.
	* Note, *assume we have more states than weights*. This assumption is founded on the fact *we have more states than actions*.
* We may do something similar for the action value function. That is 
  
  $$
  \hat{q}(s,a,w) =\approx q_\pi(s,a)
  $$
  
* We specify a **state distribution** which specifies how much we care about errors in value estimates for state $s$. We denote this with $\mu(s)$. 
	* We require this state distribution because state updates can affect other states. 
	* Making one state accurate makes the estimations for other states inaccurate.
	* We often choose $\mu(s)$ to be the fraction of time spent on $s$.

# Objective
* The objective function is called the **mean square value error (MSVE)** defined as 
  $$
  \overline{VE} = \sum_{s\in S}\mu(s) \left[v_\pi(s)-\hat{v}(s,w)\right]^2
  $$
  
	* Note *minimizing MSVE does not necessarily give optimal policies* . Our goal is always to find the best policy, not the best value function.
* We can generalize the notion of comparing policies with the following norm 
  
  $$
  ||v||^2_\mu= \sum_{s\in S}\mu(s) \ v(s)^2
  $$
  
* A geometric way to view things is where value functions are functions parameterized with weight vector $w$. *Different approaches implicitly make use of different characterizations for the solution*.
	* In a geometric view, [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]]'s solution is found by using projections towards the closest policy (as defined below using projection matrix $\Pi$. 
	  
	  $$
	  \Pi v = v_w \text{   where } w =\underset{w\in\mathbb{R}^d}{\text{argmin}}  \ ||v-v_w||^2_\mu
	  $$

	* An alternative is the **Bellman Error** obtained by substituting $v_w$ for $v_\pi$ in the [[Backups in Reinforcement Learning|Bellman equations]] and computing the difference 
	  
	  $$
	  \overline{\delta_{w}}(s) = \mathbb{E}_\pi[R_{t+1} +\gamma v_w(S_{t+1}) - v_w(S_t) \mid S_t=s, A_t\sim \pi]
	  $$
	  
	  Aka, *it is the expected [[Temporal Difference Learning|TD]]-error*.
	  
	* The vector of all Bellman errors at all states is the  **Bellman error vector**. It can be seen as a result of applying the Bellman operator to the approximate value function so that 
	  
	  $$
	  \delta_w(s) = B_\pi v_w - v_w
	  $$
	  
	* The norm of the Bellman Error vector can be used as a measure of error called the **Mean square Bellman error**
	  
	  $$
	  \overline{\text{BE}}(w) = ||\delta_w||^2_\mu
	  $$

	* In an approximation context, we only deal with representable value functions. Those that cannot be represented are instead projected onto the subspace. The **mean square projected Bellman error** measures this
	  
	  $$
	  \overline{\text{PBE}}(w) = || \Pi \delta_w||^2_\mu
	  $$

	* The **mean square return error** is the expectation, under $\mu$ of the square of the error between value estimate and return.
	  
	  $$
	  \begin{split}
	  \overline{\text{RE}}(w) &= E\left[(G_t-\hat{v}(S_t,w))^2\right] \\ 
	  &= \overline{\text{VE}}(w) + E\left[(G_t-v_\pi(S_t))^2\right]
	  \end{split}
	  $$

### Learnability
* A value function is **learnable** if given any amount of experience, we converge to the optimal / true value function. 
* 
* *The Bellman Error is not learnable* unless we have access to the underlying model itself.
* *The VE objective is not learnable* -  given two MDPs that give the same streams of experience, we cannot distinguish between them from the experience stream alone.
	* *Still, the parameter that optimizes VE is learnable*.  This follows from using the mean square return error. Observe how RE is just VE but with a variance term independent of $w$.
* *PBE and TDE are determined from data and are learnable*.  However, note they have different minima.
# Topics
* [[On Policy Prediction and Control with Approximation ]]
* [[Off Policy Prediction and Control with Approximation]]
* [[Eligibility Traces]]  - a useful (most cases mandatory) construct when it comes to function approximation
* [[Policy Gradient Methods]]
# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto]]
	* 9.1 - 9.2 - the objectives of function approximation
	* 11.4 - more on the geometry of the value function.
	* 11.6 - why the Bellman Error is not learnable.
* [[Reinforcement Learning]]