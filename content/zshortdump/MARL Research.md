* [^Wang_2022] proposes a [[Transformer Model|Transformer]]-based multi actor-critic framework for active voltage control. It also aims to stabilize the training process of [[MARL Algorithms and Approaches|MARL algorithms]] with a transformer.
	* The network operates on a power distribution network (represented as a graph). 
	* Raw observations are projected into an embedding space. Since it operates on a graph, it makes use of the adjacency matrix as additional positional information.  This information is then fed to a transformer
	* A [[Recurrent Neural Network|GRU]] is used to project the representation to an action. 
![[TMADDPG.png]]
<figcaption> Transformer-Based MADDPG. Image taken from Wang, Zhou Li (2022) </figcaption>

[^Wang_2022]: Wang, Zhou, and Li (2022) [Stabilizing Voltage in Power Distribution Multi-Agent Reinforcement Learning with Transformer](https://arxiv.org/pdf/2206.03721)


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

