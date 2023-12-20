* Systems dynamics models explore possible futures and ask [[Data Analytics|what if questions]]. We can test the value of a model by asking ourselves the following: 
	* Are the driving factors likely to unfold this way?
	* If they did, would the system react this way? 
	* What is driving the driving factors? 
* Model utility depends not on whether its driving scenarios are realistic but on whether it responds with a realistic pattern of behavior. 
* *Similar system structures exhibit similar system behaviors*. Similar feedback mechanisms imply similar dynamics. 

* System behaviors can often be surprising. Naive policies on such systems can result in counterintuitive results. 

# Stocks and Flows
* **Stocks** contain the memory of the history of changing flows within the system. They contain quantities and information accumulated over time.
* **Flows** change the quantities involve in a stock. They may either add or remove a stock.
* *The behavior of a system can be understood by understanding the dynamics of its stocks and flows*
* A weighted [[Directed Graph]] can be used to model the system's stocks and flows.


## General Principles
* As long as the sum of all inflows exceeds the sum of all outflows, the level of the stock will rise. 
* As long as the sum of all outflow exceeds the sum of all inflows, the level of the stock will fall. 
* If the sum of all outflows equals the sum of all inflows, the stock level will not change. It will be held in **dynamic equilibrium** wherein the stock does not change but resources still flow through the system. 
* A stock can be increased by decreasing the outflow rate as well as by increasing the inflow rate.  
* A stock can be decreased by increasing the outflow rate as well as by decreasing the inflow rate.  
* A stock generally changes slowly even when the flows into or out of them change suddenly. Therefore, *stocks act as delays or buffers in the system*. They can only respond to change by gradual filling or draining. 
* Changes in stocks set the pace of the system dynamics. The time delay they are associated with may cause delays but also stability. *Stocks allow inflows and outflows to be decoupled and to be independent* and temporarily out of balance with each other

* We tend to be [[Human Biases|biased towards examining inflows rather than outflows]]. 
* We also tend to underestimate the time it would take for a stock to increase.

* *Nonrenewable resources are stock-limited*. The entire stock is available at once and can be extracted at any rate (potentially limited however). But since the stock is not renewed, faster extraction rate means shorter lifetime of the resource. 
* *Renewable resources are flow-limited*. They can support harvest indefinitely but only at a finite flow rate equal to their regeneration rate. If they are extracted faster than they regenerate, they may eventually be driven below a critical threshold and become, for all practical purposes, non-renewable. There are three possible behaviors 
	* When balancing systems are fast enough to stop extraction before a critical threshold is reached, we overshoot extraction but adjust to a sustainable equilibrium 
	* When balancing systems are slower and less effective, we overshoot beyond the equilibrium followed by an oscillation around it  
	* When balancing systems are very weak and extraction only keeps growing, we overshoot and then we have a collapse of the resource. 

# Feedback 
* *When a stock either changes exponentially or stabilizes, there is a control mechanism at work.* Such a mechanism operates through a feedback loop. 
* A **feedback loop** is a closed chain of causal connections from a stock, through a set of decisions or rules or physical laws or actions that are dependent on the level of stock and back again through a flow to change a stock.
	* **Balancing / Negative** feedback loops are equilibrating or goal-seeking structures in systems and are sources of stability and resistance to change. 
	* **Reinforcing / Positive** feedback loops are self-enhancing leading to exponential growth or runaway collapse. They are found whenever a stock has the capacity to reinforce or reproduce itself.

* Feedback loops may not necessarily be effective due to delays or due to the actions triggering them not being strong enough.
* When one feedback loop dominates another, it has a stronger impact on behavior. *Complex behavior of systems often arise as the relative strengths of feedback loops shift*, causing a dominance shift. 

* *Feedback loops are everywhere*. Part of systems thinking is to be able to recognize how feedback loops can occur. 
* *A system can have many interrelated feedback loop that influence the same stocks.*

* *The information delivered by a feedback loop -- even nonphysical feedback, can only affect future behavior.* It can't deliver a signal fast enough to correct behavior that drove the current feedback. Even nonphysical information takes time to feedback into the system. 
	* *There will always be a delay in responding*. 
	* A flow will not react instantly to a flow, it will react only to a change in stock and only after a delay in registering the incoming information. 
	* Changes in the delay may (or may not depending on its type and the relative lengths of other delays) make a large change in the behavior of the system.
		* Delays that are too short cause overreaction and amplified oscillations. 
		* Delays that are too long cause damped, sustained or exploding oscillations. This can destabilize the system and cause it to collapse. 

* *A stock maintaining-balancing feedback loop must have its goal set appropriately to compensate for draining or inflowing processes that affect the stock*. Otherwise, the feedback process will fall short of or exceed the target for the stock. 
* *A delay in a balancing feedback loop makes the system likely to oscillate*. 

* In physical, exponentially growing systems, there must be at least one reinforcing loop driving the growth and at least one balancing loop constraining the growth because no physical system can grow forever in a finite environment. 
	* A quantity growing exponentially toward a constraint or limit reaches that limit in a surprisingly short time.
	* If the physical constraint is higher, the growth loop will elude the constraint loop and the convergence to the limit will be slower. 

# Links 
* [[Thinking in Systems by Meadows]] - Ch. 1 -2 