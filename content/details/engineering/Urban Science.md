# Topics
* [[Skyscrapers]]
* [[The Electricity Grid]]
* [[The Water Ways]]

# Papers
* [^Dong_2021] proposes an architecture for a smart [[Urban Science|city]] simulation platform. It consists of several services including transportation, emissions monitoring, energy consumption, and networking.

[^Dong_2021]: Dong (2021) [A Smart City Simulation Platform with Uncertainty](https://dl.acm.org/doi/pdf/10.1145/3450267.3452002)


* [^Chapman_2017] introduces a proof of concept framework for integrating stochastic multi-agent models with building planning and simulation. The aim is to bridge the gap between what is simulated in the planning phase and how the building is actually used. 
	* It combines stochastic models for occupant behavior, multi-agent reinforcement learning for more complex behaviors, and building simulation. 
	* The following stochastic models were used.
		* Models for occupant activity (i.e., cooking or cleaning)
		* Occupant state based on their current activity. (done using a [[Finite Automata and Regular Languages|Finite state machine]])
		* Occupant presence and location
		* Occupant metabolic gains based on standard physical and personal parameters
		* Window actions (when do agents open windows)
		* Shading actions (do agents illuminate or dim the household)
		* Lighting (do agents use indoor lights)
	* To simplify things, the stochastic models were tested to determine if they had a significant impact on the overall model's predictive power. *Agents are equipped with their own stochastic models to introduce heterogeneity*
	* It also makes use of the [[Belief-Desire-Intention]] model for activities not covered by existing stochastic models . 
	* Social interaction between agents is governed by agent state. Interactions can lead to conflicts which are resolved through negotiation and voting(i.e., [[Game Theory]]). Agents are assumed to be perfectly rational.
	* The quality of the simulation is augmented using [[Reinforcement Learning]]. RL is used to enable agents to learn actions and develop new stochastic behaviors, especially as an adaptation to environment changes

[^Chapman_2017]:  Chapman (2017) [Multi-Agent Stochastic Simulation of Occupants in Buildings](https://eprints.nottingham.ac.uk/39868/1/JacobChapman4170825psxjc5%2017-01-16%20final.pdf)

# Links
* [[Science and the City -- The Mechanics Behind the Metropolis by Winkless]]