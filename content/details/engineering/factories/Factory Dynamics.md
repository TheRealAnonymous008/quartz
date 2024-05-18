# Dynamics
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
  
  The PWC serves as a threshold for determining good (close to best case) and bad (close to worst case) lines.

* *Increasing the bottleneck rate will reduce the cycle time for any given WIP level*. However, this is sometimes not possible or economically practical.
	* When the bottleneck cannot be improved, we can observe gains by improving the process times of the non-bottleneck processes.

* **Labor Capacity Law** In systems where capacity is defined by labor and not equipment (i.e., labor is the bottleneck), we have the maximum capacity of a line with $n$ cross-trained operators with identical work rates as 
  
  $$
  \text{TH}_\text{max} = \frac{n}{T_0}
  $$
  Note we assume all workers work on a single job continuously (without interruption) at any given point in time.
	* This is the ideal throughput to achieve.

* In cases where workers can become blocked due to unavailable equipment, the *WIP becomes the number of workers*. 
	* Note that this assumes workers are cross-trained which may not be a valid assumption.
	* *In such cases, it makes sense to organize workers to minimize blocking -- place the fastest workers downstream*
	* In the **bucket brigade system**, when the worker farthest downstream finishes a job, they move up the line and take the job from the next worker
* *If workers are allowed to work multiple jobs, the performance will depend on how jobs are allocated*
	* One allocation metric is -- any free worker takes on the next job, prioritizing downstream jobs. Any worker blocked by a downstream job takes a new job.  *Keeping workers busy maximizes throughput. Working on downstream jobs minimizes cycle times*

* **CONWIP with Flexible Labor** -- In a CONWIP line with $n$ identical workers and $w$ jobs where $w\ge n$, any policy that never idles worker when unblocked jobs are available will achieve a throughput level $\text{TH}(w)$ bounded by
  
  $$
  \text{TH}_\text{CW}(n) \le \text{TH}(w) \le \text{TH}_\text{CW}(w)
  $$
  
  Where $\text{TH}_\text{CW}(x)$ represents the throughput of a CONWIP line with all machines staffed by workers and $x$ jobs in the system
	* The upper bound is the case when the system never has unblocked jobs so the number of workers is the determinant.
	* The lower bound is the case when the system always has blocked jobs so that workers are effectively working on $1$ job each. 
	* *If a line has significant variability, then cross training gives significant improvement* because workers can dynamically re-balance the line.

[^randomness]: Analogous to the concept of entropy from [[Information Theory]]

* **Law of Conservation of Material**. In a stable system, over the long run, the rate out of a system (i.e., throughput) will equal the rate in, less any yield loss, plus any parts production within the system. 
	* *Stability means capacity (or throughput for that matter)is strictly greater than the arrival rate*. [^conservation] Otherwise, with variability in mind, it is possible to run out of WIP unless we have infinite WIP (and infinite cycle time)
	* In practice, a stable state is achieved only when we do not allow changes in the line's parameters.
	* Yield loss occurs as a loss of product due to defects
	* Parts Production occurs when a part becomes multiple parts. 

[^conservation]: When there is no variability, an equality between these two is allowed. In practice, this is never observed.

* **Law of Capacity**. In steady state, all plants will release work at an average rate that is strictly less than average capacity. 
	* Any discrepancy to this is the result of short-term variation which gets smoothed out over the long term.
	* Since it is impossible to use 100% of plant resources in the long run, it is management's decision whether measures that add capacity or release rate are part of a planned strategy or in response to conditions going out of control

* **Law of Utilization**. If a station increases utilization without making any other changes, average WIP and cycle time will increase in a highly non-linear function. The effect of this increase is stronger when $u\to 1$.
	* This follows from the results in [[Queueing Theory]].
	* When variability is $0$, the cycle time remains constant for all utilization levels up to 100% and then becomes infeasible. In practice, this does not happen.
	* No real world station has space to build an infinite queue which limits the total amount of WIP. *This means high utilization is hard to reach*

# Batching
* A **process batch** pertains to a production process. It can be measured with either:
	* **Serial batch size** - number of  jobs in a common family are processed before the workstation is changed to another. *Its size is related to the length of a setup. More setup = more production rate needed to achieve capacity*
	* **Parallel batch size** - number of jobs produced simultaneously in a true batch workstation. *Its size depends on the  demand of the station.*

* **Transfer batch** size pertains to the number of parts that accumulate before being transferred to the next station
	* *Smaller transfer batch size = shorter cycle time = less waiting = more material handling*

* **Law of Process Batching**. In stations with batch operations or significant changeover times:
	* The minimum process batch size that yields a stable system may be greater than one.
	* As process batch size becomes large, cycle time grows proportionally with batch size.
	* Cycle time at the station will be minimized for some process batch size, which may be greater than one.

* In a serial line the arrival rate of batches with arrival rate $r_a$, and batch size $k$ is given by 
  $$
  \begin{split}
  r_a'&=\frac{r_a}{k} \\ 
  
  \end{split}
  $$
  The effective arrival time and utilization is given by 
  
  $$
  \begin{split}
  t_e&=kt + s \\
  u &= r_a' (kt +s) &= r_a\left(t + \frac{s}{k}\right)
  \end{split}
  $$
  The restriction of $u < 1$ means 
  $$
  k > \frac{sr_a}{1-tr_a}
  $$
	* If lots are not split when moved downstream (i.e., the entire batch is sent at once), then all parts wait for the other parts so that 
	  
	  $$
	  \text{WIBT}_{\text{nosplit}} = (k-1)t
	  $$
	* If lots are split when moved downstream, then the average WIBT will depend on the part's position. 
	  
	  $$
	  \text{WIBT}_{\text{split}} = \frac{k-1}{2}t
	  $$


* In a parallel line, we no longer need to worry about setup time between batch elements (because the entire batch is processed at once)
  
  The average WTBT is simply the average time between arrivals to form a batch, given by
  
  $$
  \text{WTBT} = \frac{k-1}{2r_a}
  $$
  Once $k$ arrivals have occurred, we can begin processing. We get that 
  
  $$
  c_a^2(\text{batch}) = \frac{c_a^2(\text{individual})}{k}
  $$
  The capacity is given by $k/t$. Maximum capacity is given by $B/t$. We require that effective capacity follow
  
  $$
  u=\frac{r_a}{k/t} < 1
  $$
  If $B<r_at$, then we have insufficient capacity to meet demand. 


* **Law of Move Batching**. Cycle times over a segment of a routing are roughly proportional to the transfer batch sizes used over that segment, provided there is no waiting for the conveyance device.
	* If the more often we move parts between stations, the longer they wait for the material handling device, then this additional queue time might cancel out the reduction in wait-to-batch time
	* *Cycle time reduction is possible by reducing transfer batch sizes, provided there is sufficient material handling capacity to carry out the moves without delay*. 
	* Cycle time does not increase due to process or arrival variability. 
	* Another way this can be applied is through **Cellular Manufacturing** where all workstations in a cell are positioned close to each other to minimize transfer batch sizes. 

# Time 
* The average **cycle time** at a station is the sum of the following components
	* **Move Time** - the time jobs spend being moved from the previous workstations
	* **Queue Time** - the time jobs spend waiting for processing at the station or to be moved to the next station.
	* **Setup Time** - the time a job spends waiting for the station to be setup.
	* **Process Time** - the time jobs are actually being worked on at the station.
	* **Wait-to-batch Time** - the time jobs spend waiting to form a batch for either parallel processing or moving.
	* **Wait-in-batch Time** - the average time a part spends in a process batch waiting its turn on the machine.
	* **Wait-to-match Time** - occurs at assembly stations when components wait for their mates to allow the assembly operation to occur.
* *Ever component of cycle time except process time is an inefficiency*

* Assemblies typically involve **matching operations** wherein processing cannot start until all necessary components are present. Any shortage of the components can disrupt the assembly operation so we commonly specify a **final assembly schedule**

* **Law of Assembly Operations**. The performance of an assembly station is degraded by increasing any of the following (akin to increases in variability)
	* *Number of components being assembled* because extra components add potentially variable arrival times 
	* *Variability of component arrivals*
	* *Lack of coordination between component arrivals* because this will lead to more delays and waiting time. 

* The **line cycle time** is equal to the sum of the cycle times at the individual stations less any time that overlaps two or more stations.

* The **in-process time** is the portion of cycle time not spent in the queue 
  
  The total in process time can be bound as follows assuming no variability. Jobs arrive in batch simultaneously where the first job sees a full setup at each station and jobs move one at a time through the line,
  
  $$
  \frac{k-1}{2} \min_i t(i) \le \text{total in-process time} \le \frac{k-1}{2} \max_{i} t(i)
  $$
	* In the best case (lower bound), the fastest station goes last and there is no idle time at the last station. 
	* In the worst case (upper bound), the slowest station goes  first. 

* **Law of Lead Time**. The manufacturing lead time for a routing that yields a given service level is an increasing function of both the mean and standard deviation of the cycle time of the routing.
	* From a cycle time perspective, rework is particularly disruptive.
# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 7 - 9
* [[Inventory Management and Control]]
* [[Fundamental Objects in Factory Physics]]
* [[Factory Variability]]