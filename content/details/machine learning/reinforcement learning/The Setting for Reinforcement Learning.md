# Characterizing the Problem
* *Reinforcement Learning* is an area concerned with how agents should take actions in an environment to maximize some reward. 
	* It is a part of a trend back towards simple, general principles of learning and decision making.

* The tasks in Reinforcement Learning are characterized by the following:
	* Agents exist in a closed loop system where actions influence the future inputs.
	* Agents are not told which actions to take, rather they must discover which actions yield the most reward. Such reward is not necessarily indicative of what action to take.
	* The consequences of actions play out over extended periods of time. 
	* The Exploitation-Exploration Tradeoff (see more [[The Exploitation-Exploration Trade-Off|here]]).
	* Use of [[Markov Processes in Machine Learning|Markov Processes]].

* Tasks in reinforcement learning are closer to the intended goal. *Rather than understanding the structure of the problem, we focus on achieving the task itself*. 

* In a Reinforcement Learning problem, agents always aim to maximize the reward even if they may not be able to achieve it.
* Reinforcement learning has the following elements:
	* A **policy** that defines the response of the agent given some environmental stimulus. The response comes as a probability distribution on the set of actions. The **actions** capture decisions to be learnt by the agent.
		* The **on-policy distribution** $\mu$ is the distribution of the states that is obtained from following the current policy
	* A **reward signal** defines the goal of the agent.
	  The reward signal is given by the environment and is agnostic to any agent's prior knowledge. This is done so the agent does not "decree" that it has received a good reward.
		* We denote the reward as $r$.
		* If we are dealing with the reward from going from $s_t$ to $s_{t+1}$ by taking $a_t$, we have the reward as $R(s_t,a_t,s_{t+1})$
		  
	* A **value function** specifies a function that is being optimized in the long run. It encodes the total amount of reward that can be achieved on average. *The value function dictates how an agent is to be optimized*.
		* *Domain knowledge is best put in the value function*. It can also be put in the initialization but note that the distribution may be nonstationary.

	* An **environmental model**.  The environment consists of anything the agent has no direct absolute control over. The environment has **states** which influence the actions that the agents will take, 
		* *Learning is done while interacting with the environment* 

	* Environmental **states** pertain to either immediate sensations or complex processed stimuli. The state represents what the agent receives. *States can change stochastically or deterministically*. 

* *A critical restriction in Reinforcement Learning Tasks is the fact that finding exactly optimal solutions requires high computational costs*. This is mitigated uniquely by reinforcement learning by using the appropriate approximations.

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 1 , 3 - 3.4]] - an introduction to Reinforcement Learning
* [[A Unified View on Reinforcement Learning Approaches]] - more on approaches to RL