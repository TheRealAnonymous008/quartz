* **Factory Physics** is the study of the underlying behavior of manufacturing [[System Science|systems]]. It allows us to identify optimizations, design new systems, and balance tradeoffs to coordinate policies from disparate areas.
	* Low-level operations details have always had strategic consequences for manufacturing firms.
	* The answer to the problem of operations management is *not what to do about manufacturing problems, but how to [[System Opportunities|think]] about them*
	* Factory physics is founded on -- Problem solving, Technical details, and Well-developed intuition about the manufacturing processes.
	* We make use of [[Data Analytics|prescriptive models]]  based on provided assumptions. In this sense, *all laws in Factory Physics are tautologies*. These assumptions, however, can be validated with empirical evidence.

* Factory Physics is a [[Science|scientific approach]].
	* The scientific approach gives a set of tools for understanding the system.
	* Science offers precision using the language of [[Mathematics]].
	* Science offers intuition about the world around us.
	* Science facilitates synthesis of disparate perspectives. 

* A **manufacturing system** is an objective-oriented network of processes through which entities flow. It is a [[Network Science|network]] of interacting parts. 
	* The **fundamental objective** is the broad goal everyone can agree on. *A fundamental objective balances the desires of all involved parties*.
	* Usually the fundamental objective will need to be narrowed down to establish compromises between all involved parties. Tradeoffs will also need to be done to meet conflicting objectives .
	* The fundamental metric of profit and ROI can be computed as follows
	  
	  $$
	  \begin{split}
	  \text{Profit} &= \text{Revenue} - \text{Cost} \\
	  \text{ROI} &= \frac{\text{Profit}}{\text{Assets}}
	  \end{split}
	  $$
	  
	  Revenue is generated through **throughput** -- the amount of product sold. **Assets** focus on things we can control. 
	* There are three basic assets we must be able to [[System Opportunities|control]]
		* **Information** - what is known about the system
		* **Control** - operating policies that affect system behavior.
		* **Buffers** - protections against variability

![[Manufacturing Objectives.png]]
<figcaption> The objectives of a manufacturing organization. Image taken from Hopp and Spearman</figcaption>


* We perform **operations analysis** to observe the actual system and develop a conceptual model.
* We make use of **means-end analysis** -- The objective is always specified first, and then alternatives are sought and evaluated in terms of this objective. *We seek creative alternatives and [[Lenses for the Process|brainstorming]] should cover a broad range of ideas*. 
* We also seek to optimize and iteratively [[details/creativity/design/DOET/Design Thinking|refine]] our objectives, alternatives, and models.
* We convert objectives to constraints via **satisficing**.
* Models require **verification** (checking the logic of the model) and **validation** (comparing the model to reality). 

![[Systems Approach Factory Physics.png]]
<figcaption> Systems Analysis Pipeline. Image taken from Hopp and Spearman </figcaption>

* *[[Systems and Models|Models]] allow us to quantify the tradeoffs that exist within the system.* 
* We can make use of accounting models and techniques to estimate the individual costs per product. This guides both long term and short term decisions. 
	* *The need for accounting models arise due to **overhead** - costs not associated with products*
	* *The value of limited resources depends on how they are used.* Static cost-based models cannot assign costs to limited resources
* *The primary purpose of models is to guide strategic decisions.* Use different models for different problems as appropriates. 
	* Models allow us to perform risk analysis.
	* The best policy is generally not obvious in advance

# Misc
* The **conveyor model** of Cycle Time is an improvement over [[Material Requirements Planning|MRP]]'s model of fixed cycle time. *The time to process a quantity of WIP is dependent on the capacity of the line*.
  
  $$
  \text{CT} = \max\left(T_\text{approx}, \frac{\text{WIP}}{C_\text{approx}}\right)
  $$
  Where $T_\text{approx}$ represents the time a job can go through an uncongested line, and $C_\text{approx}$ represents the capacity of the line
# Topics
* [[Inventory Management and Control]]
* [[Factory Dynamics]]
# Links 
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]]
* [[Manufacturing]]