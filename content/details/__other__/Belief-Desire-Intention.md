* The **Belief Desire Intention Model** is a model for [[Agent Based Modeling|agent programming]] where agents have 
	* **Beliefs** - the [[Bayesian Models|informational state of the agent]], including rules and heuristics that it has. 
	* **Desires** - the objectives or goals of the agent. 
	* **Intentions** - the actions that the agents have chosen to do. This presupposes planning.

* Events in the system modify the agent's beliefs, plans, and goals.
* Optionally, agents may have **Obligations** -- [[Sociology|norms and commitments]]

* The BDI architecture also provides three behavior structures
	* **Perception** - the agents can perceive their environment and update their beliefs accordingly.
	* **Rule** - a function to infer new desires or beliefs from the current desire and beliefs.
	* **Plans** - behaviors used to accomplish specific intentions.

* The general pipeline for behavior is as follows
	* Execute perceptions
	* Execute rules.
	* Check if the current intention is achieved
		* If an intention is achieved, set the current plan to NULL and remove it from the intention base
		* If the achieved intention's super-intention is on hold, it is reactivated.
	* Check if the current intention is to be kept.
	* Check for a plan
		* If there is a plan, execute it.
		* If the plan has been persistent for a while, drop it with a certain probability and formulate a new plan later.
	* Check for desires.
		* If the current intention is on hold, choose a desire as a new intention.
	* Choose a plan as a new current plan. Preferably, choose the plan with highest priority
	* Execute the plan.
	* Check if the plan was finished. 
# Links
* [[Faculties of the Mind]] -the goal of BDI is to simulate intelligent behavior
* [GAMA Platform -- BDI Architecture](https://gama-platform.org/wiki/BDIAgents_step2)