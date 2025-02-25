

* https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/


* [^miyake_2024] shows the use of MARL for analyzing and predicting the evolution of social [[Network Science|networks]].  Each node represents a rational agent in an RL setting. 
	* The goal is to design explainable reward and policy functions. Each agent's policy is to add or remove edges or change their attributes. 
	* The NetEvolve system consists of three phases:
		* Learn the reward function for each node. 
			* The reward function consists of a linear combination of interpretable features and represents the desirability of the network to each node. 
			* The weights used in the reward function are learnt. 
			* *Optimization is done by assuming that the input time series evolution of the network is optimized*. 
		* Learn the policy for each node. The policy expresses the tendency to change attributes and edges. 
		* Predict future networks based on the multi-agent simulation using learned policies.

[^Miyake_2024]: Miyake et al. (2024) [NetEvolve: Social Network Forecasting using Multi-Agent Reinforcement Learning with Interpretable Features](https://dl.acm.org/doi/pdf/10.1145/3589334.3647982)


* [^Weil_2024]  introduces a decentralized approach to MARL using a [[Graph Neural Network|graph]]-based message passing algorithm to pass agent states to their neighbors.  
	* In this approach, agents form a communication network. Agents pass their local states to their neighbors in the network, and aggregate incoming messages to form a local observation of the entire network. 
	* This approach can be used with any RL training algorithm by performing the message passing step in each episode and augmenting agent observations with the local graph observation. 

[^Weil_2024] Wel et al. (2024) [Towards Generalizability of Multi-Agent Reinforcement Learning in Graphs with Recurrent Message Passing](https://arxiv.org/abs/2402.05027)

# Top
* [[Chain of Thought Prompting]]

* [[Numerical Methods]] 
	* ODEs
	* PDEs
* [Look more into Sparse Autoencoder](https://www.youtube.com/watch?v=9-Jl0dxWQs8)
* [Proportional Navigation](https://en.wikipedia.org/wiki/Proportional_navigation)

