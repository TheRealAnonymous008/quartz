* Reinforcement Learning can be thought of as an adversarial process between generating a good policy based on a value function and generating a value function from a given policy. Both converge to the optimum.
# Topics
* [[Reinforcement Learning - Notation Guide]] - a collection of notation symbols for reinforcement learning.

* [[The Setting for Reinforcement Learning]] - gives context to the Reinforcement Learning Problem
* [[A Unified View on Reinforcement Learning Approaches]] - a broad overview on RL methods.
* [[The Exploitation-Exploration Trade-Off]] - a trade-off central to RL.
* [[Markov Processes in Machine Learning]] - perhaps the most common way to frame a reinforcement learning task. See also MDP Control for how optimal policies behave.
* [[Backups in Reinforcement Learning]] - more on Bellman Equations
* [[Dynamic Programming for Reinforcement Learning]] - for Dynamic Programming based methods on handling RL tasks.
* [[Monte Carlo Methods in Reinforcement Learning]] - for methods based on partial information about the environment.
* [[Temporal Difference Learning]] - for methods that combine DP (bootstrapping) and Monte Carlo (by learning from the environment).
* [[N-step Bootstrapping]] - generalizations of TD-learning
* [[Eligibility Traces]] - generalizations of Temporal Difference Learning that involve giving a certain amount of credit to each state for the received return.
* [[A Unified View on Planning and Learning]] - integrating dynamic programming techniques with Monte Carlo and Eligibility-traces.
* [[Decision Time Planning]] - RL-adjacent algorithms that focus on applying MC techniques to tree search.

* [[Function Approximation in Reinforcement Learning]] - how can we generalize experience with a limited subset of the state space? 
* [[Policy Gradient Methods]] - instead of optimizing value functions, we optimize parameterized policies.

* [[Multi-Agent Reinforcement Learning]]
* [[Distributional Reinforcement Learning]]
* [[Inverse Reinforcement Learning]]

* [[Applications of Reinforcement Learning ]]
# Papers
* [^Eysenbach_2018] proposes DIAYN for Hierarchical RL as a method to learn skills--latent conditioned, consistent policies, without the use of a reward function. 
	* In order to acquire skills that are useful, we must *train the skills so that they maximize coverage over the set of possible behaviors while being distinct enough from each other.*
	* The paper uses maximum entropy policies to be diverse to obtain a mixture of skills. This method is easily generalizable to other tasks. 
		* Different skills specialize in visiting different states. 
		* States are used to distinguish skills rather than actions. This way actions that have the same effect are indistinguishable. 
		* Skills are diverse and suited for complex tasks.
	* The skills can be learnt with supervision as needed.
	* Learnt skills can be used for imitating an expert. 


	![[DIAYN.png]]

	[^Eysenbach_2018]: Eyesenbach, Gupta, Ibarz, and Levine (2018) [Diversity Is All You Need: Learning Skills Without A Reward Function](https://arxiv.org/pdf/1802.06070.pdf)

* 🎯 Branching Reinforcement Learning by Du, and Chen (Jun 15, 2022) 
# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto]]
* [[Reinforcement Learning and Stochastic Optimization -- A Unified Framework for Sequential Decisions by Powell|Powell]]
* [OpenAI Spinning Up](https://spinningup.openai.com/en/latest/index.html) - has various modern algorithms
