* *Get what is needed at the time it is needed, and in the amount needed*. Every workstation acquires the required materials precisely as needed, just in time. 
* The benefits of JIT can be attributed to the use of [[Factory Design and Policy|WIP caps]].

* The **seven zeros** serve as the goal of JIT. The north star is towards zero inventories -- a metaphor for a high level of excellence and innovation.
	* **Zero Defects** - parts must be of good quality. Defects cause delays.
	* **Zero Excess lot size** - stock must be replenished as it is taken. We maximize responsiveness if workstations replace parts one at a time. 
	* **Zero Setups** - because setups cause large batch sizes, we eliminate setup times to account for frequent setups.
	* **Zero breakdowns** - no machine failures, all operators must be available. Breakdowns cause delays. 
	* **Zero handling** - material is given at the time required and in the amount required. The system will run smoothly if material is fed with no intermediate pauses. Handling causes delays.
	* **Zero lead time** - when a workstation requests parts, they are provided immediately. 
	* **Zero surging** - sudden changes in quantities of products mean delays because the system has to respond. We want level production plans and uniform product mixes. 
* No matter how well a manufacturing system is running, there is always room for improvement

* The key lessons of JIT to the broader field of manufacturing management are as follows
	* The production environment is, itself, a control
	* Operational details matter strategically. 
	* Controlling WIP is important (small cycle times)
	* Flexibility is an asset. The inflexibility of JIT is compensated for by continuously improving on flexibility
	* Quality can come first (and is more profitable)
	* Continual improvement is a condition for survival. Manufacturing as a field is dynamic.
# Implementation
* *JIT requires a precise and smooth operating system* -- small disruptions easily cascade throughout the system. 
* **Autonomation** is used to prevent disruptions
	* Machines are *automated* so one worker can operate many machines
	* Machines are *foolproofed* so they automatically detect problems.

* We use a **Master Production Schedule** to specify which products are to be produced in each time interval. *The sequence of produced products need not match customer orders*. 
	* We want the MPS to be level over time. 
	* To mitigate surges, we make use of a **Final Assembly Schedule** to specify requirements over the short term. This requires
		* *Smoothing aggregate production requirements*. 
			* This demands a **repetitive manufacturing environment** where the flow rate is kept constant and significant deviations are compensated for
		* *Sequencing final assembly*. We do this by translating product specific requirements to a production sequence.
			* *The sequence on the line should maintain the proportions of required product*. 
			* This requires **mixed model production** where lines can support multiple products. 

* *JIT requires mitigating machine failures which may cause delays*. 
	* **Capacity buffers** involve scheduling for the facility to run less than 24 hours a day. If there is a delay, the factory can catch up. If there is excess, workers are allocated other tasks. 
	* **Two shifting** - two shifts are scheduled per day separated by a down period for maintenance or catch up. 
	* *We reduce WIP so production is JIT, but we maintain excess capacity just in case*

* *JIT necessitates reducing setup times*. This is especially needed for our uniform final assembly sequence.
	* We distinguish between **internal setups** - those when the machine is stopped, and **external setups** - those when the machine can keep producing product
	* *Internal setups are disruptive to production*.
	* We have four concepts for setup reduction
		* Separate internal and external setup. Ask what tasks must be done with the machine stopped.
		* Convert as much as possible of the internal setup to external setup. 
		* Eliminate adjustment process.
		* Abolish the setup itself -- use uniform product design or parallelization. 

* *JIT works best if we have multifunctional workers who can move wherever in the plant*. 
	* We can use a **worker rotation system** where workers are rotated through various jobs and then cross-trained. This:
		* Keeps multiple skills sharp
		* Reduces fatigue and boredom
		* Fosters systems thinking for everyone
		* Increases innovation
		* Introduces flexibility
	* The layout of the factory is changed from linear to **U shaped cells**.  
		* One worker can attend to all the machines with minimum walking.
		* Many workers can occupy the cell depending on production requirements.
		* Workers can monitor inflows and outflows, facilitating JIT flow.
		* Workers can easily smooth out unbalanced operations.
* *JIT requires a high level of quality to function*. JIT highlights detects problems and identifies their sources. 
* Quality is not checked in separate stations. Workers check quality at every step of the way. *This gives [[Knowing What To Do -- Constraints, Discoverability and Feedback|better feedback]]*. 
* There are seven principles of quality 
	* *Process control* - workers themselves make sure the production processes operated properly. 
	* *Easy to see quality* - use visual displays of quality measures. They give better feedback to customers and inspectors.
	* *Insistence on compliance* - demand compliance with quality standards at every level of the system. Quality first, output second. 
	* *Line stop* - each worker had the authority to stop the line to correct quality problems.
	* *Correcting one's own errors* - no rework lines. Workers that produced the defective items fix them. 
	* *100% check* - inspect every part not just a random sample. Automate inspection if necessary. 
	* *Continual improvement* - aim for zero defects. 

* The **kanban system** works as follows. 
	* When a part is removed from the final inventory point, the last workstation in line is given authorization to replace the part. 
	* *Workstations send authorization signals upstream to replace the part just used.*
	* Toyota has formulated six rules for kanban
		* Each process issues requests (via move  cards) to its suppliers when it consumes its supplies
		* Each process produces (via production cards) according to the quantity and sequence of incoming requests.
		* No items are made or transported without a request
		* The request associated with an item is always attached to it.
		* Processes must not send out defective items.
		* Limiting the number of pending requests (i.e., WIP) makes the process more sensitive and reveals inefficiencies.
	* *The number of card counts per station dictate the level of WIP*
	* The mechanics of the kanban system is similar to [[Inventory Management and Control#Base Stock Model|the base stock model]]. Every time a part is consumed, a request is made for that many parts to be produced (in effect, a level base stock is kept).
# Limitations
* JIT is more of a philosophy that may be difficult to transport. It is more of an idea than a toolbox and firms implement it differently.
* Because it has a myriad of implementations, it is less structured than [[Material Requirements Planning]]. It requires discretion on choosing what method to use for  the business, and even then it also requires deviating from the status quo.
* JIT does not guarantee immediate improvements. *It is neither simple nor inexpensive*
* JIT's objectives can often compete with each other, which requires balancing.
* While quality is an important metric, it is far from the only important metric.
* Kanban does not [[Factory Design and Policy|scale well with a high number of parts produced infrequently]].
	* Kanban is typically only applicable in repetitive manufacturing environments where material flows along fixed paths at steady rates.
	* Kanban is not robust against swings in product mix, product complexity and volumes.
	* Optimal card count allocation is a function of mix. Hence, to achieve high throughput with low WIP, we may need to dynamically vary the card counts over time
* Kanban induces more operator stress because they must replenish voids as quickly as possible to prevent starvation.
# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 4

* [[System Science]] - JIT is systems-focused. 