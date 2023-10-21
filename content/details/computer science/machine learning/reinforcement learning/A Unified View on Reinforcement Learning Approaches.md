
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
	* Generally more complex, and subject to high variance.
	* We call the first policy as the **behavior policy** denoted $\beta$. This is the policy that is used to generate behaviors
	* We call the second policy the **target policy** denoted $\pi$. This is the policy that will become the optimal policy 
	* We require two assumptions
		* **The Assumption of Coverage**:  Every action taken under $\pi$ is also taken occasionally under $\mu$ 
		  $$\pi(a\mid s)>0\implies \beta(a\mid s)>0$$
		* **Soft Policy Assumption**: $\mu$ is a soft policy where all actions from all states may be taken. 
	* Off-policy is analogous to *learning by imitation*.

* On-policy learning is the general case of off-policy learning where the target and behavior policies are exactly the same.
# Other Dimensions
* **Returns**: Are [[The Setting for Reinforcement Learning#Tasks and Goals|tasks]]:
	* Continuing / Episodic
	* Discounted / Undiscounted.
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
	* **Asynchronous*** - updates are performed simultaneously, using whatever approximations are appropriate.
* **Real / Simualted** - do we backup on [[A Unified View on Planning and Learning#Definition of Terms|Real or Simulated Experience]] and to what extent
* **Location of Updates** - what should be updated? 
	* For Model-free - we choose only among those states / state-action pairs encountered.
	* For Model-based - we can choose arbitrarily.
* **Timing of Updates** - update done 
	* as part of selecting actions (i.e., [[Dynamic Programming for Reinforcement Learning#Value Iteration|Value Iteration]]) or 
	* after selecting actions (i.e., [[A Unified View on Planning and Learning#Trajectory Sampling|trajectory sampling]] and [[Decision Time Planning#Rollout Algorithms|rollout algorithms]])
* **Memory for updates** - how long should we retain update values.
	* Permanent retention
	* Retain only when computing an action selection (I.e., [[Decision Time Planning#Heuristic Search|heuristic search]])
* Use of [[Function Approximation in Reinforcement Learning|function approximation]].
# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 8.13]]
* [[Backups in Reinforcement Learning]] - more on sample and expected updates.