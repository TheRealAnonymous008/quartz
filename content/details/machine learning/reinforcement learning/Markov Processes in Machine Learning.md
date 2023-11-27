# The Markov Property
* The **Markov Property** pertains to the evolution of a process where the *future state only depends on the current state and not the past*.
* *For decision processes, the current state has to be informative* 
* Markov Processes can be represented using a **transition graph**, [^1] where each node is a state and each edge is a weighted edge with a transition probability attached to it. 

[^1]: See more [[Finite Automata and Regular Languages|here]].
# Markov Decision Processes
* *Caveat: Not all processes need to be Markovian to be analyzed effectively*. 
* **Markov Decision Processes** are described using actions, rewards, states and transitions.
	* An agent and environment interact at discrete time steps $t=0,1,2,3,\dots$
	* Each time step is associated with an environment **state** $S_t$.
	* An agent performs an **action** $A_t$ in response to state $S_t$.
	* A **reward** $R_{t+1}$ is given for $A_t$.
	* The sequence 
	  $$
	  S_0,A_0,R_1,S_1,A_1,\dots
	  $$
	  is called the **trajectory**.

* An MDP is **finite** if the set of states, actions, and rewards are finite. 
* The **dynamics** of the MDP is computed as a [[Probability|probability distribution]] on states and actions defined as 
  $$
  p(s',r\mid s,a) = P(S_t=s', R_t=r\mid S_{t-1} =s, A_{t-1}=a)
  $$
  In an MDP, the probability above completely characterizes the dynamics of the environment.

* These are essential in the field of Reinforcement Learning (see [[The Setting for Reinforcement Learning|here]]). *Almost all Reinforcement Learning tasks can be understood as a Markov Decision Process*.
* The value function in an MDP assuming the existence of a policy can be approximated in a variety of ways.
	* Simulation (this is cubic time complexity)
	* Analytical Derivation. 
	* Using Dynamic Programming. 

* A **Markov Reward Process** is a Markov decision process without actions. 
# Markov Decision Process Control
* In an MDP, the existence of a discounted value function implies the existence of a deterministic optimal policy. The policy need not be unique. In addition to the polices defined [[A Unified View on Reinforcement Learning Approaches|here]], the following properties are observed:
	* The policy is deterministic.
	* The policy is stationary (i.e., it does not depend on the time step. It is always applicable)
* In an MDP, the actions that appear the best (with respect to an optimal policy) after searching for one step are indeed the best. 
	* This follows immediately from the fact the process is memoryless.
	* The implication is that there is no need to plan more than one step ahead in a Markovian process. *Greedy works assuming we can find the optimal policy.* 
	* This comes at the cost that this very rarely happens in practice due to complexity and performance costs.
# Links
* [[The Setting for Reinforcement Learning]] - for an overview of the relationship between Markov Processes and Reinforcement Learning.
* [[Characterizing the Decision Problem]] - MDPs are a special case of the Decision Problem 

*  [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 3.5 - 3.6]]


