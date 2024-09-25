* Reinforcement Learning can be thought of as an adversarial process between generating a good policy based on a value function and generating a value function from a given policy. Both converge to the optimum.
# Topics
* [[Reinforcement Learning - Notation Guide]]

* [[The Setting for Reinforcement Learning]] 
* [[A Unified View on Reinforcement Learning Approaches]] 
* [[The Exploitation-Exploration Trade-Off]] 
* [[Markov Processes in Machine Learning]]
* [[Backups in Reinforcement Learning]]
* [[Dynamic Programming for Reinforcement Learning]] 
* [[Monte Carlo Methods in Reinforcement Learning]]
* [[Temporal Difference Learning]]
* [[N-step Bootstrapping]]
* [[Eligibility Traces]]
* [[A Unified View on Planning and Learning]]
* [[Decision Time Planning]]

* [[Function Approximation in Reinforcement Learning]] 
* [[Policy Gradient Methods]] 

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

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto]]
* [[Reinforcement Learning and Stochastic Optimization -- A Unified Framework for Sequential Decisions by Powell|Powell]]
* [OpenAI Spinning Up](https://spinningup.openai.com/en/latest/index.html) - has various modern algorithms
