# Definition of Terms
* **Planning Methods** pertain to those that require a model. **Learning methods** are model-free.
* A **model** is a way for the agent to make predictions about its environment, specifically how it will respond to its actions.
	* A **distribution model** produces a description of all possibilities and their [[Probability|probabilities]]. 
	* A **sample model** produces just one possibility sampled according to the underlying distribution.
	* *Distribution models are more powerful* and can be used to generate samples. However, *sampling models are easier to obtain* as they do not require computing the actual probabilities, only simulating the environment.
	* *Always note:* The Model can be wrong, as in it does not match the logic of the environment.

* A **simulated experience** is the byproduct of using the model, alongside a policy, to generate an episode. 
* The **real experience** corresponds to the model interacting with the actual  environment. 

* **Planning** is a task wherein given an input model, develop a policy for the agent.
	* **State-space planning** is where we search through state space for an optimal path to the goal (i.e., the optimal policy)
		* **Background Planning** is when we use planning to gradually improve the policy on the basis of simulated experience from a model. That is, *by decision time the "plan" is already set and all we need to do is do a lookup on a table.*
		* **Decision-Time Planning** is when we focus on a particular state to analyze different trajectories. *At decision time, we use simulated experience to select an action for a given state*.
	* **Plan-space planning** is where we search through the list of plans for the best plan. Operators transform the plan and make it optimal.

* *For state-space planning, regardless if it is model-based / model free, we have the following observations: *
	* Computing value functions as a key intermediate step toward improving the policy
	* .Compute value functions by updates or backup operations applied to simulated experience
* Planning in small, incremental steps enables JIT planning--one which can be interrupted or redirected to boost efficiency.

* There are two ways to enhance the model using experience [^1]
	* **Model Learning** pertains to using the experience to optimize the model.
	* **Direct Reinforcement Learning** pertains to improving the value function and policy directly by applying different [[Reinforcement Learning]] algorithms using the experience
		* Much simpler than indirect reinforcement learning
		* They are not prone to biases in the model.
	* **Indirect Reinforcement Learning** pertains to improving the value function and policy by planning with the model.
		* They make fuller use of a limited amount of experience.
		* They achieve a better policy with fewer interactions. 
[^1]: A diagram of the interactions can be found in [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 8]]

* **Dyna-Q** is a simple model which integrates learning and planning.
	* Planning is done by randomly sampling seen state-action pairs and performing Q-learning on simulated experiences
	* Learning is done using one step Q-learning from the real experiences
	* Assuming the world is deterministic, it builds a state-action transition graph so that if $S_t,A_t$ are observed, then $R_{t+1},S_{t+1}$ follow.
	* Assuming the world is stochastic, a state-action transition graph will still be built as before, but this will have modeling errors.
# Optimizations and Considerations
### Model Correctness
* *Models can be wrong if the environment is stochastic, non-stationary, or due to non-generalizable policies.*. 
* In some cases, the policy leads to the discovery and correction of modeling errors, especially when the model is too optimistic. The agent discovers that its model was optimistic when it sees the real experience from the environment.
* In other cases, the environment becomes better and the model needs to be updated accordingly so that it can find a new optimal policy. However, this will usually take longer to detect depending on [[The Exploitation-Exploration Trade-Off|the degree of exploration allowed]] and if any heuristics are in place.
### Prioritized Sweeping
* *Rationale:* It is inefficient to backup on all state-transition pairs when they have not changed. 
* Prioritize backing up from any states whose value has changed. We change all states that lead to this particular state. This is called **backward focusing**.
* To be more efficient, we *maintain a priority queue* based on the effect of a backup. We only update those states which meet a certain threshold in priority (i.e., those states whose values have changed a lot.)
* For stochastic models, update not based on the sample but based on expectation computed across all possible successor states (weighted with their probabilities).
* *Limitations*: It uses expected updates rather than sample updates which are computationally expensive, especially for low impact transitions.
### Backups
* We consider the type of [[Backups in Reinforcement Learning|backups]] that we perform based on computational and precision needs.
* For search spaces with large branching factors, sample backups are preferable to make faster progress, and also because the large number of sample backups ran reduces the error.
	* By causing estimates to be more accurate sooner, sample backups allow the values backed up from the successors to be more accurate.
### Trajectory Sampling
* The classical approach of **exhaustively sweeping** devotes equal time to parts of the search space, even though only certain subsets of the space are likely to be of high value.
* Another approach is to simulate starting from a state and following a policy. Then, we backup along the trajectory (that is, *perform an update on all state / state-action pairs encountered during simulation*) . This is called **trajectory sampling** and we sample from the **on-policy distribution** (i.e., the distribution observed from following the policy).
	* It is easy to generate.
	* In fact, trajectory sampling is an efficient way to sample from the on-policy distribution because it is invariant to sudden changes in the policy.
	* It also ignores parts of the state space that are bad or uninteresting or that are unlikely to actually show up (it can even leave these states with no value)
	* However, *without the assurance of exploration, trajectory sampling limits itself to few states, which are themselves, possibly suboptimal*.
		* Hence, for short-term learning, on-policy only sampling is fine. But for long-term sampling, we may consider exhaustive sweeps.


# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 8]]
	* 8.2 - for more on DynaQ, an algorithm which presents a simple integration of planning and learning.

* [[Dynamic Programming for Reinforcement Learning]] - for more on model-based methods
* [[Eligibility Traces]] - for more on model-free methods.
* [[The Exploitation-Exploration Trade-Off]] - one concern is the fact we need to balance improving the model and working with the current model
* [[Decision Time Planning]] 