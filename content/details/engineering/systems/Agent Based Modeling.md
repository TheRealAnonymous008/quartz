* An **Agent Based Model (ABM)** is a computational model that involves simulating the agents, and their actions and interactions within a system with the goal of understanding large scale behaviors and outcomes.

* ABMs are useful for studying [[Complex Systems|complex systems]] especially those that feature [[Emergence|emergent structures or phenomena]].  It allows for analyzing systemic behaviors from the bottom up.

* ABMs are primarily motivated by difficulties in modeling phenomena via mathematical or or conceptual models.

# Theory
* *Incorporate heterogeneity* within the system. Rather than having representative agents for large clusters of agents, embrace the heterogeneity. [^axtell_2022]
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

* [^pangallo_2024] suggests we should also consider data driven ABMs. 
	* The recent trend toward data-driven ABMs is helping overcome their traditional limitations of lacking mathematical rigor and feeling arbitrary because of difficulties in calibration.
		* The data driven approach can replace unnecessary assumption
		* They can also help make reasonable assumptions by measuring which assumptions improve results (i.e., how they match real world data).
	* *ABMs are data driven when the parameters in the ABM are obtained based on empirical data*.
	* Generally there are three methods for making ABMs more data driven
		* **Calibration** involves modifying the parameters to match empirical data. For parameters where there is no source of empirical or theoretical data, we can infer the data via [[Machine Learning|a machine-learning like process]]
			* Sampling guesses for these parameters
			* Using summary statistics from simulated and real data
			* Defining a loss function to compare simulated and real data.
			* Choosing parameters to minimize loss.
		* **Initialization** involves estimating agent-level attributes and initial conditions.
			* Initialization requires to make disparate sources of data compatible with themselves and with the model.
			* Some procedures include
				* Generating synthetic populations
				* Reconstructing a [[Network Science|network]] (if given). 
				* Use data, if not from the target source, something analogous to the target source.
		* **Assimilation** involves estimating the entire time series of agent-specific variables.
			* Use a [[Kalman Filter|Kalman filter]] to combine models and observations.
			* Use [[Probabilistic Graphical Models|PGMs]]. 
			* Use [[Metaheuristics|heuristics]]

![[Data Driven ABMs.png]]
<figcaption> Data Driven ABM typology. Image taken from Pangallo and del Rio-Chanona (2024) </figcaption>

[^Pangallo_2024]: Pangallo and del Rio-Chanona (2024) [Data Driven Economic Agent-Based Models](https://arxiv.org/html/2412.16591v1)

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


[^Axtell_2022]: Axtell  and Farmer (2022) [Agent-Based Modeling in Economics and Fin ance](https://oms-inet.files.svdcdn.com/staging/files/JEL-v2.0.pdf)

# Links
* [[Game Theory]]
* [[Network Science]]
* [[Machine Learning]]