* Also known as **MRP II**. It aims to address the issues of [[Material Requirements Planning]] while integrating more functions to the system. This includes

![[MRP II.png]]

<figcaption> MRP-II System. Image taken from Hopp and Spearman </figcaption>

## Components
* **Long Range Planning** - involves planning within ranges of half a year or more. 
	* **Forecasting** - aims to predict [[Scarcity, Supply, and Demand|demand]] in the future. This includes both long range forecasting of part families and short range forecasting for individual end items. 
	* **Resource Planning** - determines capacity requirements over the long term. We feed projected available capacity to aggregate planning
	* **Aggregate Planning** - determines levels of production and inventory for each part family. 

* **Intermediate Planning** - from the aggregate planning module, we get a detailed forecast of anticipated orders. We make use of **Available To Promise** to allow the planner to know which orders on the MPS are committed, and which are available to promise to new customers, and to react to demand (i.e., via pricing).
	* **Master Production Scheduling** - takes the demand forecasting and firm orders and generates an anticipated build schedule at the highest level of planning detail. This generates the demands used for MRP. 
		* A **final assembly schedule** determines when the exact end items are produced while the master production schedule is used to schedule models.
		* A **superbill of material** contains forecast percentages for the different options of each particular model
	* **Rough-cut capacity planning** provides a capacity check of a few critical resources to ensure the feasibility of the master production schedule It makes use of a **bill of resources** for each end item. This BOR gives the *number of hours required for each critical resource* (including the times for each subresources required)
		* *RCCP can give a conservative estimate* since we do not perform netting.
		* *RCCP can give an optimistic estimate* since it does not perform offsetting and assumes production can be completed in a single period
	* **Capacity Requirements Planning** - provides a more detailed capacity check.
		* It performs **infinite forward loading** to predict job completion times for each process center, using given fixed lead times, and then computes a predicted loading over time. The loading is compared to capacity.
		* Even when load exceeds capacity, *CRP assumes the time to go through the process center does not change*. [^crp]
		* *CRP is not a good predictor beyond the very near term*.
		* CRP does not provide good tracing capabilities to find the sources of problems. *CRP cannot remedy overloaded situations*.
		* *It implicitly assumes infinite capacity* because of fixed lead times independent of the load of the process center. *There are better alternatives to this*.
		* *It has large data requirements and voluminous outputs*
	* **Material Requirements Planning** - the same as [[Material Requirements Planning|the one specified here]]. It releases the job pool consisting of PORs. 
* **Short-Term Control** - focuses on implementing the plans from the previous models. 
	* **Job Release** - converts PORs to scheduled receipts. It also allocates parts for use in assembling other parts. 
	* **Shop Floor Control** - tracks internal manufacturing. 
		* **Job Dispatching** - develops a rule for arranging the queue in front of each workstation that both maintains due date integrity, keeps machine utilization high, and manufacturing times low. [^job_dispatch]
			* **Shortest Process Time** - jobs with the shortest job time are done first. It decreases average manufacturing time, increases machine utilization, but does not consider the due date.
			* **Earliest Due Date** - jobs that are closest to the due date are done first. It has good performance when jobs are of the same size, but not better than SPT.
			* **Least Slack** - jobs with least slack first. Slack is due date minus remaining process time minus current time.
			* **Least Slack Per Remaining Operation** - jobs with least slack divided by number of operations left.
			* **Critical Ratio** - compute an index as follows
			  
			  $$
			  \text{index} = \frac{\text{due date} - \text{current time}}{\text{hours remaining}}
			  $$
			  Jobs with the smallest value first.
		* *No job dispatching rule is perfect. All are [[Data Structures and Algorithms|greedy]]*. 

		* **I/O Control** - it provides an easy way to check remaining releases against available capacity. 
			* It aims to control lead times by doing the following
				* Monitor the WIP level in each process center
				* If WIP goes above a certain level, current release rate is too high.
				* If it goes below a certain level, the current release rate is too low.
				* If WIP stays within control levels, the release rate is just right.
				* All changes must be done by changing the MPS.
			* *By waiting until WIP levels have become excessive, the system has, in many respects, already gone out of control.*

[^crp]: In practice, this is inaccurate because more load usually means more time. 
[^job_dispatch]: This is analogous to [[Multiprogramming]] systems and how they handle threads.

## Enterprise Resources Planning
* ERP systems are linking information together in ways that make it much easier for upper management to have a more global picture of operations in almost real time
* Compared to MRP II, it offers
	* Integrated functionality
	* Consistent UI
	* Integrated [[Database|databases]]
	* Single vendor and contract.
	* A unified architecture and tool set.
* It has the following disadvantages
	* Incompatibility with existing systems
	* Long and excessive implementation
	* Incompatibility with existing management practices
	* Loss of flexibility to use tactical point systems
	* Long product development and implementation cycles.
	* Long payback period
	* Lack of technological innovation.
* The success of ERP is at least partly due to three coincident undercurrents preceding its development -- namely *supply chain management*,  *business process reengineering* so that management is more willing to change, and *distributed processing of computers.*

* A **manufacturing execution system** is an automated implementation of shop floor control. 
# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 3