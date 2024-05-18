
* Manufacturing environments vary greatly with respect to their process structure -- the manner in which material moves through the plant *The decision of what process structure to use depends on expected [[Scarcity, Supply, and Demand|demand]] and volume*
	* **Job Shops** - Small lots are produced with a high variety of routings through the plant. Flow through the plant is jumbled, setups are common. This setup allows for more customizability and is *more suited for products with high customizability, low volumes, and slower rates.*
	* **Disconnected Flow Lines** - Product batches are produced on a limited number of identifiable routings (i.e., paths through the plant). Although routings are distinct, individual stations within lines are not connected by a paced material handling system, so that inventories can build up between stations. *Used to make similar items on a repeat basis, where the volumes are not high enough to allow for a connected line flow*
	* **Connected Flow Lines**  - The classic Assembly line. Product is fabricated and assembled along a rigid routing connected by a paced material handling system. *Suited for a narrow product range where production can be automated to produce high volumes of standardized at a faster rate*
	* **Continuous Flow Processes**  flows automatically down a fixed routing, no longer divided into discrete units. *Suited for very high volume, commodity products*. 

# Push and Pull

* In a **push production control system**, work releases are scheduled in advance based on customer due dates (demand), but must respond to changes in the plant
	* Production is triggered by a schedule.
	* *Push systems control throughput and observe WIP*
	* As soon as work on a part is complete at a workstation, it is "pushed" to the next workstation. 
	* All machines work as long as they have the parts.
	* *It is typically made to order*
	* A push system requires higher WIP levels to attain a given throughput level. 
	* Push systems are not flexible because of being prone to high WIP and low flexibility (because design changes cannot be incorporated in time.)
	* Setting release dates in a push system involves looking at capacity, which is not as simple. *Push systems are not easily observable and hence harder to optimize*
	* In a push system, WIP levels are independent of one another which makes *cycle times more variabile*.
	* *Push systems are easier to plan for*.

* In a **pull production control system**, work releases are authorized based on changes in the plant, but must be adjusted for customer due date.
	* Production is triggered by demand.
	* *Pull systems control WIP and observe throughput*
	* An operator requires both parts and an authorization signal to work
	* *It is typically made to stock *
	* *The main benefit of a pull system is that there is a limit on the maximum amount of inventory in the system*. Any disruptions do not cause WIP to grow beyond a predetermined level and gives more predictable flows (cycle time)
	* *Pull systems are flexible* because they can easily adjust to changes by reducing costs due to these changes.
	* *Pull systems have better timing of work releases*
	* Low WIP levels (independent of how this is achieved) also promote more effective quality control since we only need to inspect fewer jobs.
	* We can also perform work aheads when plant conditions are favorable (up to a certain limit of reasonability. For example, we do not want to work on tasks with speculative requirements). 
	* *Pull systems are easily observable* all we have to look for is the WIP. 
	* *Pull systems introduce negative correlation between WIP levels at different stations*. This dampens variability. 

* In a hybrid approach, the factory can be divided into push and pull segments connected via **push-pull interfaces**.
	* *The choice of where to put push-pull interface is important*
	* The closer the push-pull interface is to the customer, the less lead time we have at the cost of flexibility. 
	* The options for positioning the push-pull interface are strongly affected by the process itself.
	* The economics of push-pull interface placement are affected by how the product is customized as it progresses through the system
		* Having fewer end items may make it feasible to put the interface at the finished goods.
		* Having many items makes it more feasible to put the interface at the start [^interface]
	* In a system in which the product becomes increasingly customized as it progresses down the line, moving the push-pull interface upstream can reduce the amount of safety stock that needs to be carried as protection against demand [[Factory Variability|variability]]

[^interface]: Otherwise we have to deal with combinatorial explosion since we would need appropriate inventory for many end items.


* **CONWIP (Constant Work In Process)** is a protocol where a new job is introduced to the line each time a job departs. *CONWIP results in a WIP level that is very nearly constant*. This assumes two things (subject to extension) 
	* The production line consists of a single routing, along which all parts flow.
	* Jobs are identical so WIP can be measured in units.
* Compared to [[Just In Time Manufacturing|Kanban]], CONWIP is easier to control since we do not need cards for each station. 
	* In Kanban, cards are part number specific. In CONWIP, cards are line specific (cards are instead matched against a backlog). CONWIP scales much better when there are many parts.
	* CONWIP requires steady volume but is more robust than kanban compared to product mix. 
* A CONWIP system resembles a closed queueing network where customers never leave. 
* In CONWIP, *bottlenecks are seen more easily as places where WIP accumulates*
* *CONWIP subjects operators to less pacing stress* since authorization for intermediate materials is implicitly provided. [^stress]

[^stress]: Still, the first operator in the line has to fill voids to meet WIP. This is unavoidable just as in a regular kanban line.

* We can make use of a **Mean Value Analysis Model** where we examine the average behavior assuming all other $w-1$ jobs are evenly distributed according to the average behavior.
	* Each station is treated as if they behaved like a [[Queueing Theory|M/G/1 queues]]. The average time a job spends in station $j$ in a system with $w$ jobs remaining is given by the following (using MVA)
	  
	  $$
	  \begin{split}
	  \text{CT}_j(w) &= \mathbb{E}[\text{remaining process time}] + (\mathbb{E}[\text{no of jobs at station}] - \mathbb{E}[\text{no of jobs in service}])t_e(j) + t_e(j)\\
	  \text{CT}_j(u) &= \frac{t_e^2(j)}{2} [c_e^2 (j) -1] \ \text{TH}(w-1) + \left[\text{WIP}_j(w-1) + 1\right]t_e(j) \\
	  \text{CT}(w) &= \sum_{j=1}^n \text{CT}_j(w)\\
	  
	  \text{WIP}_j(0) &= 0 \\
	  \text{TH}_j(0) &= 0 \\
	  \text{TH}(w) &= \frac{w}{\text{CT}(w)} \\
	  \text{WIP}_j(w) &= \text{TH}(w) \ \text{CT}_j(w)
	  \end{split}
	  $$

* **Law of CONWIP Efficiency**. For a given level of throughput, a push system will have more WIP on average than an equivalent CONWIP.
	* For a given level of throughput, a push system will have longer average cycle times than an equivalent CONWIP system. 

* **Law of CONWIP Robustness**. A CONWIP system is more robust to errors in WIP level than a pure push system is to errors in release rate.
	* If we tried to plot profit as a function of WIP level, we find that the curve is relatively flat

## Shop Floor Control
* Shop Floor Control encompasses a variety of functions
	* **Material Flow Control** - we decide which jobs to release into the factory, which parts to work on at individual workstations, and what material to move between workstations.
	* **WIP Tracking** - involves identifying the current location of parts in the line.
	* **Status Monitoring** - surveillance of other parameters in the line besides WIP position (i.e., machine and staffing status)
	* **Throughput Tracking** - measures the output against an established production quota and/or customer due dates which dictates if we need overtime.
	* **Statistical Throughput Control** - allows us to track progress towards meeting the production quota.
	* **Capacity Feedback** - ensures that high level planning modules are consistent with low-level execution. It also lets us estimate capacity.
	* **Quality Control** - allows us to address reworks which require parts and may add delays. 
	* **Work Forecasting** - anticipates the expected amount of work needed. It should consider the effects of delays from rework or yield loss. 
# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 10

* [[Fundamental Objects in Factory Physics]]
* [[Factory Optimization Techniques]]
* [[Control Theory]]
