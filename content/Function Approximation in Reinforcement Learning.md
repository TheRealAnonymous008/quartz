* *Rationale*: We often have memory constraints that do not allow us to explore large state spaces. Hence we sample from a small state space.
	* However, we need a way to make decisions on unsampled states using those that we have sampled. This is done via **function approximation
	* This is, in fact, [[Supervised Learning]]. It makes changes generalizable but controlling them more complex.
		* *It should be noted, that we must make use of 
	* It also make it extensible to **partially observable problems** where states are not fully visible to the agent.
	* It cannot augment states with memories of past observations.
# Prediction
* Estimates and Update rules in Reinforcement learning can be formulated with the following formula (analogous to gradient descent): $$\text{New} = \text{Old} + \text{Step} \left[ \text{Target} - \text{Old} \right]$$We notate this with $\text{OLD}\mapsto \text{NEW}$ 


# Topics
* [[On Policy Prediction and Control with Approximation ]]
# Links
* [[Reinforcement Learning]]