* An **Agent Based Model (ABM)** is a computational model that involves simulating the agents, and their actions and interactions within a system with the goal of understanding large scale behaviors and outcomes.

* ABMs are useful for studying [[Complex Systems|complex systems]] especially those that feature [[Emergence|emergent structures or phenomena]].  It allows for analyzing systemic behaviors from the bottom up.

* ABMs are primarily motivated by difficulties in modeling phenomena via mathematical or or conceptual models.

# Theory
* *Incorporate heterogeneity* within the system. Rather than having representative agents for large clusters of agents, embrace the heterogeneity.
* *Matching the scale of a model to the data* can be important
* *Move beyond rational agents*. Incorporate limited information and bounded rationality. A typology of agents can be found below:
	* **Simple agents** - the behavior is mostly random but there is a goal. Agents do not maintain internal models and only react to the environment based on immediate self interest
	* **Learning Agents** - agents maintain a model of the environment.
		* **Individual Learning** - agents learn data from the environment  and update its internal model
		* **Social Learning** - agents build models of other agents or individual agents.
		* **Group Learning** - agents learn to behave as a group.
	* **Behavioral Agents** - agents which are made to reproduce the results of experiments. This also allows us to *scale from lab results to simulation results*.
	* Other Agents include
		* **Cognitive Agents** where agents have [[Faculties of the Mind|cognitive abilities]]
		* **Emotive Agents** - agents with simulated [[Emotion|emotions]] that can affect their decision processes
		* **Deontic Agents** -agents that can form their own goals out of obligation or social norms.

* *Match the actual processes being simulated*. 
* *Model the agent interactions*. Some methods include:
	* [[Network Science|Networks]]
	* Agent interaction regimes -- only some agents are active at any given time step.  
		* *This avoids perfect synchrony which has some advantages*
			* It avoids meaningless artifacts in the model output
			* The real world is often asynchronous.
		* Some common regimes:
			* **Uniform Activation** - agents are activated sequentially. To avoid artifacts, ensure the order is randomized.
			* **Random Activation** - agents have a random chance of being activated. 
			* **Poisson clock activation** - agents are active based on a schedule determined via a Poisson distribution. 
		* It is also possible to have endogenous activation where agents decide when to be active.

* *Explore hierarchies* within the system. 
* *Explore emergent superstructures that form* as a result of agent interactions.
* *Consider incorporating real world data*
	* Use agent models to qualitatively reproduce aggregate patterns.
	* Use agent models to quantitatively reproduce aggregate data.
	* Use agent models to quantitatively reproduce micro-data.

* The common pipeline for creating an ABM is:
	* Design the model and the theory behind it.
	* Codify the rules of the model into code.
	* Hyperparameters tuning and validation
	* Model analysis
## Opportunities and Challenges
*  Incorporate micro-data to the model itself.
* Model the full population of the system.
* Optimization - in particular considering [[Computer Organization|hardware]] and [[Multiprogramming|parallelism]].
* The Curse of Dimensionality  - more parameters in the ABM give rise to exponential search spaces 
* Using ABM for forecasting.
* Using ABM as a teaching tool.

# Applications
* Some historic models:
	* The Schelling model for modeling segregation.
	* The Axelrod model of the iterated prisoner's dilemma
	* Traffic and Pedestrian Flow models.
	* [[Epidemiology|Epidemiology]] models (i.e the SRI model). 
	* Ecological models (i.e., Predator Prey)
	* [[Politics|Political]] models
		* International relations
		* Voting dynamics
	* [[Sociology|Sociological]] models
		* Demography
		* Dynamics of propagating cultural behavior.
		* Simulating societies
		* Modeling inequality.
	* [[Urban Science|Urban dynamics]]

* [[Computational Economics]]


# Links
* [[Game Theory]]
* [[Network Science]]
* [[Machine Learning]]