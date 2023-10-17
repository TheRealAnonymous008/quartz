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
	* A **reward signal** defines the goal of the agent.
	  The reward signal is given by the environment and is agnostic to any prior knowledge. This is done so the agent does not "decree" that it has received a good reward.
	* A **value function** specifies a function that is being optimized in the long run. It encodes the total amount of reward that can be achieved on average. *The value function dictates how an agent is to be optimized*.
		* *Domain knowledge is best put in the value function*. It can also be put in the initialization but note that the distribution may be nonstationary.

	* An **environmental model**.  The environment consists of anything the agent has no direct absolute control over. The environment has **states** which influence the actions that the agents will take, 
		* *Learning is done while interacting with the environment* 

	* Environmental **states** pertain to either immediate sensations or complex processed stimuli. The state represents what the agent receives. *States can change stochastically or deterministically*. 

* *A critical restriction in Reinforcement Learning Tasks is the fact that finding exactly optimal solutions requires high computational costs*. This is mitigated uniquely by reinforcement learning by using the appropriate approximations.
# Tasks and Goals
* *The goal of Reinforcement Learning is to maximize the expected return by changing the agent's policy*. 

* The **return** is quantified as *a function of the reward* that the agent receives. *It is a measure of the cumulative performance of the agent on a particular task* 
	* In **episodic tasks** the agent receives rewards in series before eventually the environment is reset to its starting state. One run is called an **episode**. The length of an episode is called its **horizon**.
	* In **continuous tasks** the agent continually receives rewards and there is no reverting back to an original state. 

* The expected return makes use of a **discount** such that future rewards are worth less than current rewards. 
* The value function that is being optimized, is the expected return (under a policy $\pi$)
	* A **state-value function** is one that quantifies the expected return given the agent started at a particular state. This is also called the **V-function** (denoted with $V(s)$).
	* An **state-action-value function** is one that quantifies the expected return given the agent started at a particular action and state. This is also called the **Q-function**  (denoted $Q(s,a)$)
		* With respect to a policy, the value at an action assumes that all future actions taken will be optimal.

* *For episodic tasks, the calculation will terminate with an absorbing state which will continuously just give a reward of $0$. 
* Thus, the **discounted return** $G_t$ with discount rate $\gamma$ is calculated as $$G_t=\sum_{k=0}^{\infty}\gamma^k R_{t+k+1}= R_{t+1}+\gamma G_{t+1}$$
	* For episodic tasks, we simply set all rewards after the episode end $T$ as $0$.
# Links
* [[$Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 1 , 3 - 3.4]] - an introduction to Reinforcement Learning
* [[A Unified View on Reinforcement Learning Approaches]] - more on approaches to RL
* [[Monte Carlo Methods in Reinforcement Learning]] - for more on Off-Policy methods which make use of importance sampling.