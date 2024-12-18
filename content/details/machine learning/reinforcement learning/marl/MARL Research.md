* [^Waseem_2024] present a MARL approach for Flexible Manufacturing systems that can process multiple product types. 
	* The paper addresses the problem of scheduling when the environment complexity increases and when product types require distinctive workflows.
	* The paper proposes a combination of [[Static Games of Complete Information|Game Theoretic]] and MARL-based approaches 
		* A Nash game handles the interactions between robots to design collaboration cost functions.
		* A MADDPG system determines the actions of each agent. 
		* The overall action of each agent is dependent on the strategy chosen in the Nash game and by the MADDPG policy. 

[^Waseem_2024]: Waseem and Chang (2024) [From Nash Q-learning to nash-MADDPG: Advancements in multiagent control for multiproduct flexible manufacturing systems](https://www.sciencedirect.com/science/article/pii/S0278612524000530)

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

* [^kaven_2024] proposes a MARL-based approach for Lineless Mobile Assembly Systems.
	* The paper addresses the following related problems
		* The layout problem (since Mobile Assembly systems have a flexible factory layout). The goal is to determine the layout plan and minimize the cost of rearranging facilities.
		*  Job shop [[Scheduling Problem]]. In particular, the Flexible Job Shop Problem. 
	* The control approach used is an asynchronous, cooperative, heterogeneous MARL
		* The control algorithm determines the placement of stations (coordinates of the station in the environment) and the scheduling of jobs
		* The Discrete Event Simulator requests decisions from the RL algorithm. 
			* The layout planner solves the layout problem by computing the placement of each station per decision step, given the state vector (as encoded by the encoder)
			* The scheduling agent solves the flexible job shop problem. The agent computes the next station, process pairing for each job.
	* The paper uses Multi agent PPO.


[^Kaven_2024]: Kaven et al. [Multi agent reinforcement learning for online layout planning and scheduling in flexible assembly systems](https://link.springer.com/article/10.1007/s10845-023-02309-8)

* [^Wang_2022] proposes a [[Transformer Model|Transformer]]-based multi actor-critic framework for active voltage control. It also aims to stabilize the training process of [[MARL Algorithms and Approaches|MARL algorithms]] with a transformer.
	* The network operates on a power distribution network (represented as a graph). 
	* Raw observations are projected into an embedding space. Since it operates on a graph, it makes use of the adjacency matrix as additional positional information.  This information is then fed to a transformer
	* A [[Recurrent Neural Network|GRU]] is used to project the representation to an action. 
![[TMADDPG.png]]
<figcaption> Transformer-Based MADDPG. Image taken from Wang, Zhou Li (2022) </figcaption>

[^Wang_2022]: Wang, Zhou, and Li (2022) [Stabilizing Voltage in Power Distribution Multi-Agent Reinforcement Learning with Transformer](https://arxiv.org/pdf/2206.03721)

* [^ardon_2022] propose an [[Agent Based Modeling|ABM]] network that is compatible with the use of [[Multi-Agent Reinforcement Learning|MARL]] .  The framework encodes the following
	* Partial Observability. 
	* A network model for inter-agent relationships.  Connectivity can either be static or stochastic. 
	* Agent Utility Functions encapsulated as [[Game Theory - Games|types]].
	* Heterogeneous Agent Preferences
	* Support for complex turn orders (i.e., turns based on types)

[^Ardon_2022]: Ardon et al. (2023) [An RL driven multi-agent framework to model complex systems](https://arxiv.org/pdf/2210.06012)


* [^Queralta_2020] gives a survey for multi-robot search and rescue systems. 
	* Typical agents in SAR include
		* UAVs - Unmanned Aerial Vehicles. Typically characterized by cameras as sensors due to their size and weight. 
		* UGVs - Unmanned Ground Vehicles. Typically characterized with dexterous manipulation capabilities and robust against uneven terrain
		* USV - Unmanned Surface Vehicles. They operate on the water's surface.
		* UUV - Unmanned Underwater Vehicle. They operate underwater. 
	* *Interoperability is one challenge in SAR robotics* where different types of agents coordinate with each other.
	* Common environments for SAR can be divided into three: Maritime, Urban, and Wilderness.
	* Common challenges for multi-agent SAR include
		* Visual detection especially over vast areas of search or low visibility settings.
		* Long distance operation
		* [[Agent Loocalization|Localization]] / SLAM considering unknown, unstructured environments
		* Establishing long-term communication, and transmitting messages over potentially long distances.
		* Large search areas.
		* Navigation over uneven or unforgiving terrain.
	* Some avenues for research include:
		* Victim identification, Human condition awareness and triage protocols
		* Human-Swarm Interaction and Collaboration
		* Multi-Agent Coordination, including task allocation, path planning, area coverage, exploration, and general planning (both in a centralized and decentralized manner)
		* Online Learning
		* Multi-Objective, Multi-Agent optimization.
		* Agent Perception (see [[Computer Vision]]). 
		* Making solutions less computationally heavy.
		* [[Multimodal Models|Multimodal]] Information fusion
		* **Active Perception** - agents develop an understanding of "why" it senses, chooses "what" to perceive, and then "how, when and where" (see [[Belief-Desire-Intention|an analogous system]])
		* Shared Autonomy
		* Closing the gap between simulations and reality.
		* Heterogeneous swarms that are
			* Interoperable -- different kinds of robots can coordinate with each other
			* Ad hoc -- the types of robots are not predefined
			* Situationally aware -- agents are aware of the variety of robots being used. 


[^Queralta_2020]: Queralta et al. (2020) [Collaborative Multi-Robot Search and Rescue: Planning, Coordination, Perception, and Active Vision](https://ieeexplore.ieee.org/document/9220149?denied=)