* *We can optimize throughput as follows:*
	* *Increase bottleneck rate *
	* Increase bottleneck utilization by reducing blocking and starving.
		* *Buffer the bottleneck with WIP* by increasing the buffer size of the system (either by expanding it or reducing queue times). For maximum effect, we should prioritize the spaces immediately in front of and immediately after the bottleneck
		* *Buffer the bottleneck with capacity* by increasing the effective rates of non-bottleneck stations. Generally, we want to target the highest utilization non-bottleneck station
			* Faster stations upstream make starving less frequent.
			* Faster stations downstream make blocking less frequent. 


* In a system where setups are long but processes are close together, it might make good sense to keep process batches large and transfer batches small. This practice is called **lot splitting** and can significantly reduce the cycle time
* *We can use large process batches in conjunction to setup time reduction to keep utilization, cycle time and WIP under control*
* If setup times can be made sufficiently short, then using serial batch sizes of one can reduce cycle times. Otherwise, cycle time is sensitive to process batch size
* For parallel batch operations, the cycle time is significantly affected by batch size.

* *We can optimize cycle time as follows*.
	* *Reduce queue time* -- queue times are caused by utilization and variability so we have two options for policies
		* *Reduce utilization* by increasing the effective rate at the bottleneck (either increasing bottleneck rate or reducing flow into the bottleneck)
		* *Reduce variability* in either process times or arrival times, prioritizing high-utilization stations.
	* *Reduce process batch time* which is driven by the choice in process batch size.
		* *Batch optimization* to balance batch time with queue time due to high utilization.
		* *Setup reduction* to allow smaller batches without increasing utilization.
	* *Reduce Wait to match time* which is driven by a lack of synchronization of component arrivals at an assembly station.
		* *Fabrication variability reduction* to reduce the volatility of arrivals to the assembly (i.e., by reducing queue times)
		* *Release synchronization* using scheduling techniques and shop floor control.
	* *Increase Station overlap time* using lot splitting or streamlined material handling (via cellular manufacturing)

* *Satisfying customer needs is primarily about lead time (quick response) and service (on-time delivery). 
	* We should favor make-to-stock systems rather than make-to-order.
	* Alternatively, we can make generic components to stock and assemble to order. 
	* The main driver for lead time is the cycle time, so reducing cycle time also helps reduce lead time. 


* Improving a manufacturing system is not simply a matter of removing constraints. There is also a [[Management and Group Dynamics|people aspect]] to consider.

# Planning Framework
* Problems at different levels of the organization require different levels of detail, modeling assumptions and planning frequency
* Planning and analysis tools must be consistent across levels. A planning framework has the following steps [^planning]
	* Divide the system appropriately in both temporal and spatial scales. Wider planning horizons require lower level of detail.
	* Identify links between the divisions. The links should be simple.
	* Use [[System Dynamics|feedback]] to enforce consistency.



* We can disaggregate the entire production system across different time and spatial scales.
* In the temporal scale, we can divide the planning horizon broadly into long (strategic), intermediate (tactical) and short (control) scales.

| Time Horizon | Representative Decisions                                                                                                                                                                                                                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Strategy     | Financial Decisions<br>Marketing Strategies<br>Product Designs<br>Process Technology Decisions<br>Capacity Decisions<br>Facility Locations<br>Supplier Contracts<br>Personnel Development Programs<br>Plant Control Policies<br>Quality Assurance Policies |
| Tactics      | Work Scheduling<br>Staffing Assignments<br>Preventive Maintenance<br>Sales Promotions<br>Purchasing Decisions                                                                                                                                              |
| Control      | Material Flow Control<br>Worker Assignments<br>Machine Setup Decisions<br>Process Control<br>Quality Compliance Decisions                                                                                                                                  |


* We can categorize various aspects of the plant as follows:
	* Processes
	* Products
	* People

## Forecasting
* **First Law of Forecasting**: Forecasts are always wrong.
* **Second Law of Forecasting**: Detailed forecasts are worse than aggregate forecasts.
* **Third Law of Forecasting**: The further into the future, the less reliable the forecast. 

* *Decisions are made using forecasting. These decisions should be robust with respect to forecasted estimations*.
* In any forecasting environment, situations will arise in which the forecaster must override the quantitative model with qualitative information.

* **Quantitative Forecasting** is based on the assumption that the future can be predicted using numerical measures of the past in some mathematical model.
	* **Causal Models** - predict a future parameter as a function of other parameters. [^causal]
	* **[[Time Series Analysis|Time Series]] Models** - predict a future parameter as a function of past values of that parameter.
[^causal]: A good example is [[Linear Models#Linear Regression|linear regression]]

## Pull Planning
* Pull systems are harder to plan for because they are rate driven. It is hard to know the actual rates until the system is ran. 


* The **conveyor model** of Cycle Time is an improvement over [[Material Requirements Planning|MRP]]'s model of fixed cycle time. *The time to process a quantity of WIP is dependent on the capacity of the line*.
  
  $$
  \text{CT} = \max\left(T_\text{approx}, \frac{\text{WIP}}{C_\text{approx}}\right)
  $$
  Where $T_\text{approx}$ represents the time a job can go through an uncongested line, and $C_\text{approx}$ represents the capacity of the line

	* It is based on the observation that pull systems maintain fairly steady WIP levels, so the speed of the line is constant.
	* The line can  be parameterized with the **practical production rate** $r_b^P$ and the **minimum practical lead time** $T_0^P$ which indicate the *anticipated throughput and minimum lead times*. 
	  
	  We have that
	  
	  $$
	  W = r_b^P \times T_0^P
	  $$
	  The time a job is completed is then provided by
	  
	  $$
	  l = \frac{n}{r_b^p} + T_0^P
	  $$

![[Hierarchical Pull Planning Framework.png]]

* **Capacity / Facility Planning** concerns how much and what kind of equipment to purchase, how to lay out, staff, power, and support them.  It also concerns
	* *Product Lifetimes* - how long do we anticipate making the product. This influence capacity.
	* *Vendoring Options* - do we make or buy certain products and components. We can note the following
		* It is not solely dependent on cost. 
		* Consideration should be given to the long term. 
		* When the make-or-buy decision concerns whether or not to make the product at all, then it is clearly a capacity planning decision
	* *Pricing* - a valid [[Scarcity, Supply, and Demand|economic analysis]] should take into account the price of products.
	* *Time Value of Money* - capital generally means better capacity and equipment. We should take into account [[Money|interest and depreciation rates]].
	* *Reliability and Maintainability* - all things being equal, we want mean time to failure to be big and mean time to repair to be small.
	* *Bottleneck Effects* - capacity increases at bottleneck resources typically have a larger effect on throughput. 
	* *Congestion Effects* - variability degrades performance, so we should also consider non-bottleneck resources. 

* **Workforce Planning** - determines what workforce is needed to support production., considering how much and what kind of labor is available as constrained by [[Labor Market Theory|labor policies]]. We should take into account the following
	* *Worker availability* - take into account leave and training time that reduce worker availability.
	* *Workforce stability* - a firms' ability to recruit qualified people, and its overall workplace attitude, can be strongly affected by changes in the size of the workforce.
	* *Employee training* - training new recruits costs money and takes the time of current employees. 
	* *Short term flexibility* - workforce planning needs to look beyond the production plan to consider the unplanned contingencies with which the system can cope.
	* *Long term agility* - the workforce is a key source of agility -- allowing the plant to reconfigure the system for efficient production.
	* *Quality improvement* - establishing [[Quality-Based Manufacturing|quality oriented]] techniques should be incorporated to workforce planning.

* **Aggregate Planning** specifies how much of the product to produce over time subject to constraints [^agg]

[^agg]: We can do this with something like [[Linear Programming]]

* **WIP/Quota Setting** translates the aggregate plan to [[Control Theory|control]] parameters. 
	* **WIP setting** - we do not need complex models for WIP levels. We only need to set a desired WIP level. Adjustments to WIP should be done infrequently to ensure adjustments are done based on long-term estimates. 
	  
	  The WIP level can be set by taking into account a desired cycle time, and the practical production rate $r_b^P$
	  
	  $$
	  \text{WIP} = r_b^P \times \text{CT}
	  $$
	* **Quota setting** means establishing a periodic quantity of work that we will almost always complete during the quota period. This means
		* Production during the period stops when the quota is reached. 
		* Overtime is used at the end of the period to make up any shortage that occurred during regular time.
		* We can achieve a steady output
	* Quota setting should take into account cost and capacity .

* **Demand Management** allows us to filter and adjust customer orders that produces a manageable MPS. *This gives us control of the environment by smoothing out production for a smoother rate.*. 
	* Demand management should take into account manufacturing capabilities. 

* **Sequencing** provides a schedule that governs release times of work orders and materials and then facilitates their movement through the factory. 

* **Shop Floor Control** uses the work schedule as a source of general guidance -- adhering when possible and adjusting when necessary.

* *Real time simulation using simplified models provides a good tool for analysis, diagnosis, and optimization*. 

* **Production Tracking** is responsible for tabulating and displaying data regarding production, especially operations which failed. 

## Shop Floor Control
* A well-designed SFC module both controls the flow of material through the plant and makes the rest of the production planning system easier to design and manage

# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]]
	* Ch. 13 - discussion on planning frameworks
* [[Fundamental Objects in Factory Physics]]
* [[Factory Dynamics]]
* [[Factory Variability]]