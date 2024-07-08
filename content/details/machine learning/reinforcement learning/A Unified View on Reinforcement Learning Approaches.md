
| Characterization | Approach |
| --- | --- | 
| Sample Updates, Uses Bootstrapping | [[Temporal Difference Learning]] |
| Sample Updates, No Bootstrapping | [[Monte Carlo Methods in Reinforcement Learning\|Monte Carlo]] |
| Expected Updates, Uses Bootstrapping | [[Dynamic Programming for Reinforcement Learning\|Dynamic Programming]]|
| Expected Updates, No Bootstrapping | Exhaustive Search
* Note the above are extremes RL approaches are a spectrum (as seen in [[Temporal Difference Learning#N-Step Bootstrapping|n-step bootstrapping]]) approaches.
* Regardless, all approaches make use of [[Dynamic Programming for Reinforcement Learning#Generalized Policy Iteration|Generalized Policy Iteration]]
# Model-based and Model-Free
* A **model-based** approach captures the ability to *plan* (i.e., to decide the course of action by considering the future states before they are experienced).
* A **model-free** approach captures the ability to learn by *trial and error* 
# Off vs On Policy Learning
* **On-policy learning** evaluates and improves the policy that is being used to make the decisions by simultaneously making an optimal value function.
	* These policy creates only one policy that *compromises between exploration and exploitation* by creating a near optimal policy that still explores.
	* Generally simpler than off-policy and they converge faster.
	* On policy methods generally start stochastic but shift to being deterministic. These include **$\epsilon$-greedy policies** which sometimes select the non-optimal policy.
	* A variant is **soft policies** for which $\pi(a\mid s)>0$ for all states and actions $s,a$, but where the policy gradually shifts to a deterministic optimal policy.
	* These policies *iterate towards the optimal policy directly from experience*.

* **Off-policy learning** creates an optimal policy by learning from another policy. This is despite the current policy or value function being suboptimal.
	* Off-policy learning *provide a solution to the Exploration-Exploitation trade-off* by having the behavior policy explore, and the target policy exploit.
	* Generally more complex, and subject to high variance since we learn based on data that is closely related to the target..
	* We call the first policy as the **behavior policy** denoted $\beta$. This is the policy that is used to generate behaviors
	* We call the second policy the **target policy** denoted $\pi$. This is the policy that will become the optimal policy 
	* We require two assumptions
		* **The Assumption of Coverage**:  Every action taken under $\pi$ is also taken occasionally under $\beta$ 
		  $$
		  \pi(a\mid s)>0\implies \beta(a\mid s)>0
		  $$
		* **Soft Policy Assumption**: $\beta$ is a soft policy where all actions from all states may be taken. 
	* Off-policy is analogous to *learning by imitation*.
	* *It allows the agent to learn from multiple sources in parallel*. By having many target policies that learn correspond to different things.

* Off-policy learning is the general case of on-policy learning where the target and behavior policies are exactly the same.

# Tasks and Goals
* *The goal of Reinforcement Learning is to maximize the expected return by changing the agent's policy*. 

* The **return** is quantified as *a function of the reward* that the agent receives. *It is a measure of the cumulative performance of the agent on a particular task* 
	* In **episodic tasks** the agent receives rewards in series before eventually the environment is reset to its starting state. One run is called an **episode**. The length of an episode is called its **horizon**.
	* In **continuous tasks** the agent continually receives rewards and there is no reverting back to an original state. 

* The return is quantified differently based on different algorithms. The two most common formulations are given below. Most RL algorithms extend these definitions.
## Discounted Formulation
* The expected return makes use of a **discount** such that future rewards are worth less than current rewards. 
* The value function that is being optimized, is the expected return (under a policy $\pi$)
	* A **state-value function** is one that quantifies the expected return given the agent started at a particular state. This is also called the **V-function** (denoted with $v(s)$ or $V(s)$).
	* An **state-action-value function** is one that quantifies the expected return given the agent started at a particular action and state. This is also called the **Q-function**  (denoted $q(s,a)$ or $Q(s,a)$)
		* With respect to a policy, the value at an action assumes that all future actions taken will be optimal.
	* We have the following for policy $\pi$
	  $$
	  \begin{split}
	  v_\pi(s) &= \mathbb{E}_\pi[G_t\mid S_t=s] \\ 
	  q_\pi(s,a) &= \mathbb{E}_\pi(G_t\mid S_t=s, A_t=a)
	  \end{split}
	  $$
	  

* *For episodic tasks, the calculation will terminate with an absorbing state which will continuously just give a reward of $0$. 
* Thus, the **discounted return** $G_t$ with discount rate $\gamma$ is calculated as
  $$
  G_t=\sum_{k=0}^{\infty}\gamma^k R_{t+k+1}= R_{t+1}+\gamma G_{t+1}
  $$
  
	* For episodic tasks, we simply set all rewards after the episode end $T$ as $0$.

## Generalized Discounted Return Formulation
* In this case, we vary $\gamma$ at each time step, denoting the particular value as $\gamma_t$. 

* The return is defined more generally as 

$$
\begin{split}
G_t &= R_{t+1} + \gamma_{t+1}G_{t+1} \\ 
&= \sum_{k=t}^\infty \left(\prod_{i=t+1} ^k \gamma _i \right) R_{k+1}
\end{split}
$$

And to assure all sums are finite, we have that $\prod_{k=t}^\infty \gamma_k = 0$ with probability one.

* *Rationale:* It enables episodic settings and algorithms to be presented in terms of a single stream of experience. 
	* What would be terminating states are now states at which $\gamma(s)=0$ and which transitions to the start distribution.
	* We can also include **pseudo-termination** cases where we predict quantities without altering the flow of the Markov process.

## Average Reward Formulation
* Applies to continuing problems. However, there is no discounting. 
* The quality of a policy is defined as the average rate of reward (i.e **average reward**) which is given as $r(\pi)$ 
  
  $$
  \begin{split}
  r(\pi)  &= \lim_{h\to \infty} \frac{1}{h} \sum_{k=1}^h \mathbb{E}[R_t\mid S_0,A_{0:t-1}\sim \pi] \\
  
  &= \lim_{t\to \infty} \mathbb{E}[R_t \mid S_0,A_{0:t-1} \sim \pi] \\ 
  
  &= \sum_{s}\mu_\pi(s) \ \sum_{a}\pi(a\mid s) \sum_{s',r} p(s',r\mid s.a) \ r
  \end{split}
  $$
  
  Where
  
  $S_0$ denotes the initial state
  
  $A_{0:t-1}$ denotes the sequence $A_0,A_1,\dots,A_{t-1}$. 
  $\mu_\pi(s)$ is the steady-state distribution given by 
  
  $$
  \mu_\pi(s)=\lim_{t\to\infty} P(S_t=s\mid A_{0:t-1}\sim\pi)
  $$
  
  independent of $S_0$ (i.e., the [[Markov Processes in Machine Learning|Markov Process]] is ergodic).
  
  * The **steady-state distribution** is the special distribution $\mu_\pi$ under which selecting actions according to $\pi$ means we remain in the same distribution 
    
    $$
    \sum_{s}\mu_\pi(s) \sum_a \pi(a\mid s) \ p(s'\mid s, a) = \mu_\pi(s)
    $$

* Returns are defined in terms of differences between rewards and average reward. This is called the **differential return** 
  
  $$
  G_t = R_{t+1}-r(\pi) + R_{t+2}-r(\pi) + \dots
  $$
* The corresponding value functions are known as **differential value functions**, which we still denote $v_\pi$ and $q_\pi$. 
	* *Notation*: We will be explicit when we are dealing with differential value functions, but by default assume we aren't in a average reward value function context
# Forward vs Backward
* In the **forward view** we perform updates based on the next $n$ rewards and states $n$ steps ahead in the future. This is the approach in [[Temporal Difference Learning]].
* In the **backward view**, we look backward to recently visited states. This is achieved via [[Eligibility Traces]].
* Both views are equivalent and one can transform from one to the other
# Action-Based vs Policy Based
* **Action-value methods** learn the values of actions and then select actions based on the estimated values.
* **Policy-Based methods** learn a parameterized policy that can select actions without consulting a value function (this is thee approach for [[Policy Gradient Methods]])
# Other Dimensions
* **Value Estimated**: Which do we estimate?
	* Action values
	* State values
		* Use a model for action selection.
		* Use a policy for action selection.
	* Afterstate values.
* **Action Selection / Exploration**
	* How do we address [[The Exploitation-Exploration Trade-Off]]
* **Synchronous / [[Dynamic Programming for Reinforcement Learning#Optimizing DP|Asynchronous]]**: 
	* **Synchronous** - all updates are performed one by one in order.
	* **Asynchronous** - updates are performed simultaneously, using whatever approximations are appropriate.
* **Real / Simulated** - do we backup on [[A Unified View on Planning and Learning#Definition of Terms|Real or Simulated Experience]] and to what extent
* **Location of Updates** - what should be updated? 
	* For Model-free - we choose only among those states / state-action pairs encountered.
	* For Model-based - we can choose arbitrarily.
* **Timing of Updates** - update done 
	* as part of selecting actions (i.e., [[Dynamic Programming for Reinforcement Learning#Value Iteration|Value Iteration]]) or 
	* after selecting actions (i.e., [[A Unified View on Planning and Learning#Trajectory Sampling|trajectory sampling]] and [[Decision Time Planning#Rollout Algorithms|rollout algorithms]])
* **Memory for updates** - how long should we retain update values.
	* Permanent retention
	* Retain only when computing an action selection (I.e., [[Decision Time Planning#Heuristic Search|heuristic search]])
* Use of [[Function Approximation in Reinforcement Learning|function approximation]] 
* Use of [[Policy Gradient Methods]] and extensions of the Policy Gradient Theorem .
# Prediction and Update
* Estimates and Update rules in Reinforcement learning can be formulated with the following formula (analogous to [[Optimization Algorithms in Machine Learning#Gradient Descent|Gradient Descent]]): 
  $$
  \text{New} = \text{Old} + \text{Step} \left[ \text{Target} - \text{Old} \right]
  $$
  We notate this with $\text{OLD}\mapsto \text{NEW}$ 
# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 8.13]]
	* 10.3 - on Average Reward Formulation
* [[Backups in Reinforcement Learning]] - more on sample and expected updates.