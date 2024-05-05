# Fundamental Objects
* A **workstation** is a collection of one or more machines or manual stations that perform essentially the same function. 
	* **Process-Oriented layouts** mean that workstations are physically organized organized according to the operations they perform.
	* **Product-Oriented Layouts** mean that workstations are organized in lines making specific products
* A **part** is a piece of raw material, subassembly or assembly that is worked on at the workstation. All parts used in the production of end items are listed in the bill of material. 
	* **Raw Material** refers to parts purchased outside the plant.
	* **Components** are individual pieces assembled into more complex products.
	* **Subassemblies** are assembled units that are further assembled into more complex products.
	* **Assemblies** are fully assembled products or end items. 
	* **End items** are parts sold directly to a customer.
* A **consumable** are materials used in workstations but do not become part of the sold product. Consumables are not listed in the bill of material.
* **Routing** describes the sequence of workstations passed through by a part
* An **order** is a request from a customer for a particular part number, in a particular quantity, to be delivered on a particular due date.
* A **job** refers to a set of physical materials that traverses a routing, along with the associated logical information for their assembly.

* **Raw Material Inventory** pertains to the physical inputs at the start of the process.
* **Crib Inventory** is a stock point at the end of a routing for intermediate inventory.
* **Finished Goods Inventory** is a stock point for end products. 
* **Work In Process** is the inventory between the start and end points of a product routing (but not including the start and end stock points). The WIP is not necessarily equal to the crib inventory.

* The **throughput** $\text{TH}$ is the average (non-defective) output of a production process per unit time.
* The **capacity** is the upper limit on the throughput of a production process.  
	* The station capacity can be computed as 
	  
	  $$
	  \text{Capacity} = \frac{\text{No of machines}}{\text{Process Time}}
	  $$
	* In most cases, releasing work into the system at or above the capacity causes the system to become unstable
	* A line is **balanced** if all workstations have equal capacity.
* **Inventory turns** pertain to a measure of efficiency with which inventory is used.
* The **turnover ratio** is the ratio of throughput to average inventory.
* The **cycle time** $\text{CT}$ of a given routing is the average time from release of a job at the beginning of the routing until it reaches an inventory point at the end of the routing
* The **lead time** of a given routing or line is the time allotted for production of a part on that routing or line. Because it is time allotted, it is controllable.
* The **service level** of a line is defined as 
  $$
  \text{Service Level} = P(\text{Cycle Time} \le \text{Lead Time})
  $$
* The **fill rate** is defined as the fraction of orders that are filled from stock
* The **effective production rate** is the maximum average rate at which the workstation can process parts.
* The **utilization** of a workstation is the fraction of time it is not idle for lack of parts
  
  $$
  \text{Utilization} = \frac{\text{Arrival Rate}}{\text{Effective Production Rate}}
  $$

* The **bottleneck rate** of a line, denoted $r_b$ is the rate of the workstation having the highest long-term utilization. Long term means averaging out variances due to unforeseen events. *This dictates maximum throughout and capacity. 
	* In lines with a single routing, the bottleneck will be the line with the least long term capacity. This does not apply for more complicated routings.
* The **raw process time**, denoted $T_0$ is the sum of the long-term average process times of each workstation in the line. Alternatively, it is the average time it takes a single job to traverse an empty line. 
	* Over the long term, it includes infrequent delays. 
	* Over the short term, it includes the most frequent delays.
	* *This dictates minimum cycle time*
* The **Critical WIP** of a line, denoted $W_0$ is the WIP level for which a line having no variability achieves maximum throughput with minimum cycle time.
  
  $$
  W_9 = r_b \ T_0
  $$
	* *In a balanced line, $W_9$ is equal to the number of machines on the line
	* *In an unbalanced line* $W_0 < \text{No of Machines}$. Some machines are not fully utilized.

* The **state** of the system is a complete description of the jobs at all stations.
	* All states are equally likely when the following are met
		* The line is balanced
		* All stations are composed of single machines
		* Process times must be random and occur in an [[Probability Distributions Zoo|exponential distribution]]. The distribution must satisfy the [[Markov Processes in Machine Learning#The Markov Property|Markov Property]]
# Dynamics
## Key Metrics
* **[[Queueing Theory|Little's Law]]** states that for any production line ^little
  $$
  \text{WIP} = \text{TH} \times \text{CT}
  $$
  An increase in WIP generally implies an increase in throughput and an increase in cycle time.
	* When we are below capacity, we are operating with low throughput but minimal cycle time.
	* When we are above capacity, we are operating with maximal throughput but suboptimal cycle time. 
	* Assuming constant throughput, reducing WIP reduces cycle time. 
	* We can derive from this that *the number of inventory turns (CT) is the reciprocal of the average residence time (TH) of inventory  (WIP) in the system*.

[^little]: In actual Queueing Theory terms, WIP represents the average number of customers, TH represents the average effective arrival rate and CT represents the average time spent by customers in the Queue. 

* *In the best case scenario* with no variability, the minimum cycle time  for a given WIP level $w$ is given by
  
  $$
  \text{CT}_\text{best} = \begin{cases}
  T_0 & \text{if } w \le W_0 \\
  \frac{w}{r_b} & \text{otherwise}
\end{cases} 
  $$
  
  The maximum throughput for a given WIP level $w$ is given by
  
  $$
  \text{TH}_\text{best} = \begin{cases}
  \frac{w}{T_0} & \text{if } w \le W_0 \\
  r_b & \text{otherwise}
  \end{cases}
  $$

	* *The ideal is reached at the critical WIP* $W_0$. 

* *In the worst case scenario* with no variability, the maximum cycle time for a given WIP level $w$ is given by
  
  $$
  \text{CT}_\text{worst} = w T_0 
  $$
  The minimum throughput for a given WIP level $w$ is  given by
  
  $$
  \text{TH}_\text{worst} = \frac{1}{T_0}
  $$
	* *The worst case is achieved when wait time is maximized 
	* The worst case occurs when the processing times for each machine is as variable as possible.
	* The worst case can also result from batch moves.

* *Randomness means more system states are visited*. A system in **maximum randomness** will visit all states [^randomness]
	* The performance of a line is improved by ensuring fewer states are visited. This means -- 
		* Unbalanced lines (i.e., more capacity)
		* Parallelization 
		* Non-Markovian / Exponentially distributed process times. This can be achieved by reducing wait times or by reducing variability.
* The **Practical Worst Case (PWC)** cycle time for a given WIP level is given by
  $$
  \text{CT}_\text{PWC} = T_0 + \frac{w-1}{r_b}
  $$
  The **Practical Worst Case** throughput for a given WIP level is given by 
  $$
  \text{TH}_\text{PWC} = \frac{w}{W_0+w-1}r_b
  $$
  The PWC is given by assuming that jobs are uniformly distributed on the line.

* *Increasing the bottleneck rate will reduce the cycle time for any given WIP level*. However, this is sometimes not possible or economically practical.
	* When the bottleneck cannot be improved, we can observe gains by improving the process times of the non-bottleneck processes.

* In systems where capacity is defined by labor and not equipment (i.e., labor is the bottleneck), we have the maximum capacity of a line with $n$ cross-trained operators with identical work rates as 
  
  $$
  \text{TH}_\text{max} = \frac{n}{T_0}
  $$
  Note we assume all workers work on a single job continuously (without interruption) at any given point in time.
* In cases where workers can become blocked due to unavailable equipment, the *WIP becomes the number of workers*. 
	* Note that this assumes workers are cross-trained which may not be a valid assumption.
	* *In such cases, it makes sense to organize workers to minimize blocking -- place the fastest workers downstream*
	* In the **bucket brigade system**, when the worker farthest downstream finishes a job, they move up the line and take the job from the next worker
* *If workers are allowed to work multiple jobs, the performance will depend on how jobs are allocated*
	* One allocation metric is -- any free worker takes on the next job, prioritizing downstream jobs. Any worker blocked by a downstream job takes a new job.  *Keeping workers busy maximizes throughput. Working on downstream jobs minimizes cycle times*
	* In a CONWIP line with $n$ identical workers and $w$ jobs where $w\ge n$, any policy that never idles worker when unblocked jobs are available will achieve a throughput level $\text{TH}(w)$ bounded by
	  
	  $$
	  \text{TH}_\text{CW}(n) \le \text{TH}(w) \le \text{TH}_\text{CW}(w)
	  $$
	  
	  Where $\text{TH}_\text{CW}$ represents the throughput of a CONWIP line with all machines staffed by workers and $x$ jobs in the system

[^randomness]: Analogous to the concept of entropy from [[Information Theory]]
## Variability
* While Little's Law can tell us overall performance (esp. when comparing with the PWC), it does not tell us the sources of inefficiency within the line.
# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 7 - 9
* [[Inventory Management and Control]]