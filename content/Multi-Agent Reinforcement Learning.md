# Problem Statement 
* [^Yang_2021] We formulate the MARL problem using an extension of [[Markov Processes in Machine Learning|MDPs]]. 
* A **stochastic [[Game Theory|game]] is defined as a set of key elements $(N, S, \{A^i\}_{i\in \{1,\dots, N\}}, \  p \ , \{R^i\}_{i\in \{1,\dots, N\}}, \gamma)$
  
  $N$ is the number of agents. 
  $S$ is the set of environmental states shared by all agents. 
  $A^i$ is the set of actions of the $i$-th agent. The set of all action configurations is denoted $\mathbb{A}=\mathcal{A}^1\times\dots\times \mathcal{A}^N$ 
  $p:S\times\mathbb{A}\to S$ for each time step $t\in N$ gives the **transition probability** from state $s$ to $s'$
  $R^i: S\times \mathbb{A} \to S$ is the reward function for the $i$-th agent
  $\gamma\in [0,1]$ gives the discounting factor. 
  
  As a convention, we use the superscript $a^i$ for the $i$-th agent and $a^{-i}$ for all other agents. 

* In this context, *all agents simultaneously make decisions (we have a static game)*. Each agent aims to find a policy $\pi^i$ so that its reward function is maximized. 

## Challenges 
* Most algorithm for single-agent RL cannot be extended as *MARL has intrinsic non-stationarity due to the environment changing with agent actions.
* The environment needs to be accurately modeled.
* Agent goals may be significantly different to each others. Policy sharing becomes more difficult. 
* Scalability. More agents means more work needed
* It is hard to define optimality for a MARL environment. 

## Subtypes
* MARL can either be **cooperative** wherein agents work together; **competitive** where the game is zero-sum or a mix of the two. 
* Another distinction is whether the learning centralized or decentralized
	* **Centralized** models involve each agent pooling experience feeding back to a single learner. Policies are them returned for local execution. 
		* In effect, *we have more agents to help with experience* 
		* All agents have similar policies 
		* For this, [[Deterministic Policy Gradient#DDPG|DDPG]] plus a centralized learning - decentralized execution approach works (called **MADDPG**). This mixes DDPG's mode-free stability with the centralized approach. This also requires considering the outcome of the choices of all other agents. 
		* We can have a *local independent actor, but a centralized critic*. 
	* **Decentralized** or DEC-MDP models have execution and learning happening locally. 
		* This allows *adaptation to local perception of the environment*. 
		* A decentralized approach helps when there is an asymmetry in what agents can do. 
		* There are two challenges with this: nonstationarity ,partial observability ,and the inability to use standard replay buffers. 
# Research 
### VM3-AC
* [^Kim_2023] introduces a new mutual information framework for MARL. This leads to the development of an algorithm called **Variational Maximum Mutual Information, Multi-Agent Actor Critic** which allows agents to coordinate simultaneous actions without latency. 

[^Yang_2021]: Yang and Wang (2021). [An Overview of Multi-agent Reinforcement Learning from Game Theoretical Perspective](https://arxiv.org/pdf/2011.00583.pdf)

[^Kim_2023]: Kim, Cho, Jung, and Sung (2023). [A Variational Approach to Mutual Information Based Coordination for Multi-Agent Reinforcement Learning](https://arxiv.org/pdf/2303.00451.pdf)

# Links 
* [[Reinforcement Learning]]
* [[Reinforcement Learning -- Industrial Applications of Intelligent Agents by Winder]] 