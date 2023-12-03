* [^Sert_2020] combines reinforcement learning techniques with [[Agent Based Modeling|ABM]] technique to study the dynamics of segregation. 
	* *Contribution*: Combining [[Multi-Agent Reinforcement Learning|MARL]] and ABM to create an artificial environment to observe potential and existing behaviors associated to rules of interactions and rewards.  
	* In particular, the rewards each agent receives constitutes the following:
		* *Segregation reward* to promote segregation. 
		* *Interdependence reward* to promote interactions among agents of a different kind. 
		* *Vigilance reward* to promote the agent staying alive. Added to incentivize the agent to stay alive to collect more rewards.
		* *Death reward* to punish agents who lose to interactions against agents of the opposite kind. 
		* *Occlusion reward* to punish agents moving to an area occupied by agents of the same kind. 
		* *Stillness reward* to punish agents for staying still. 
	* Spatial segregation diminishes as more interdependencies among agents of different kinds are added in the same fashion as if agents are tolerant to one another
	* Older agents tend to be more segregated than younger agents. 


[^Sert_2020]: Sert, Bar-Yam, Morales (2020). [Segregation dynamics with reinforcement learning and agent based modeling](https://www.nature.com/articles/s41598-020-68447-8)


# Links 
* [[Reinforcement Learning]]