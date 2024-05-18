* While Little's Law can tell us overall performance (esp. when comparing with the PWC), it does not tell us the sources of inefficiency within the line. These inefficiencies are the result of **[[Random Variables and Probability Distributions|variability]]**. 
	* **Controllable Variation** occurs as a result of decisions. 
	* **Random Variation** occurs as a consequence of events beyond our control. 
* In light of variability, *the goal is robust policies*. 
* However, *the goal of business is ROI not reducing variability. Not all variability is bad*

## Metrics
* *The primary metric for variability is the coefficient of variation*
	* Low variability ($c < 0.75$) tends to occur in process times without adjustments.
	* Moderate variability ($0.75 \le c < 1.33$) tends to occur in process times with short adjustments (i.e., setups)
	* High variability $(1.33\ge c)$ tends to occur in process times with long outages (i.e., failures). 

* The **availability** $A$ is defined using the **mean time to failure** $m_f$ and the **mean time to repair** $m_r$
  
  $$
	  A = \frac{m_f}{m_f + m_r}
	  $$
* The **natural process time** $t_0$ is the mean process time (cycle time with no external variability)
* The **effective mean process time** $t_e$ is derived from adjusting the natural process time to account for availability.
  
  The variance and SCV $\sigma_e^2, c_e^2$ of the effective process times can also be calculated accordingly assuming repair times are sampled from the same distribution with mean and variance $m_r, \sigma_r^2$
  
  $$
  \begin{split}
  t_e &= \frac{t_0}{A} \\
  \sigma_e^2  &= \left(\frac{\sigma_0}{A}\right)^2 + \frac{(m_r^2 + \sigma_r^2 )(1-A)t_0}{Am_r} \\
  c_e^2 &=  c_0^2 + (1-c_r)^2 A(1-A) \frac{m_r}{t_0}
  \end{split}
  $$
  
  An alternative formulation can be done for non-preemptive outages by assuming the machine processes an average of $N_s$ parts between setups. Each setup has mean duration $t_s$ and CV of $c_s$. The probability of doing a setup after any part is equal. 
  
    $$
  \begin{split}
  t_e &= t_0 + \frac{t_s}{N_s}\\
  \sigma_e^2  &= \sigma_0^2 + \frac{\sigma_s^2}{N_s} + \frac{N_s-1}{N_s^2} t_s^2 \\
  c_e^2 &=  \frac{\sigma_e^2}{t_e^2}
  \end{split}
  $$
  
* The **effective capacity rate** is, then, defined with the effective mean process time in mind. $m$ denotes the number of machines
  
  $$
  r_e = A r_0 = \frac{m}{t_e} = A\frac{m}{t_0}
  $$

* The **arrival rate** $r_a$ describes the arrivals to a workstation in jobs per unit time. The **mean time between arrivals**, denoted $t_a$, is the average time between arrivals. They are related by
  
  $$
  r_a = \frac{1}{t_a}
  $$
  We can also define the **arrival CV** denoted $c_a$.

* The **mean time between departures** and **departure rate** describe departures from a workstation, denoted $t_d$ and $r_d$ respectively and related by
  
  $$
  r_d = \frac{1}{t_d}
  $$
  We also define a **departure CV** denoted $c_d$

## Sources
* **Natural Variability** is the variability inherent in natural process time, which excludes downtimes, setups or any external influence.
	* There is typically more natural variability in a manual process than in an automated one.
	* We denote the natural variability with $c_9$.
* **Preemptive Outages** occur whether we want them or not. They pertain to unscheduled downtimes that occur during the job.
	* They inflate the mean and standard deviation more than other sources of variability.
* **Non-preemptive Outages** are downtimes which inevitably occur but for which we have control when. These typically occur between jobs.
* **Recycle Variability** comes from quality control where we check if a task was done correctly and if not, repeat the task. The additional processing time adds variability. Its effect, however, is similar to non-preemptive outages.
* **Flow Variability** reflects the cascading effects of variability, where variability in one workstation induces variability on all downstream workstations.
	* A workstation is said to keep up with arrivals when $r_e > r_a$
	* A low arrival CV indicates regular arrivals. High arrival CV indicates bursty arrivals.
	* In a serial production line without yield loss or rework, the following relation holds for the $i$-th machine
	  
	  $$
	  \begin{split}
	  t_a(i+1) &= t_d(i) \\ 
	  c_a(i+1) &= c_d(i)
	  \end{split}
	  $$
	  that is, the arrival time for the next machine is the departure time for the previous.
	* Effective process times satisfy
	  $$
	  t_e < \frac{m}{r_a}
	  $$
	* We can use utilization as an interpolation parameter for the departure CV.
	  
	  When the number of machines $m=1$
	  
	  $$
	  c_d^2 = u^2 c_e^2 + (1-u^2)c_a^2
	  $$
	  
	  And more generally 
	  
	  $$
	  c_d^2 = 1 + (1-u^2)(c_a-1) + \frac{u^2}{\sqrt{m}}(c_e^2-1)
	  $$
	   
	* Flow variability can have multiple causes
		* A workstation is fed by multiple sources
		* The interarrival times follow an exponential or memoryless distribution
		* Batch arrivals -- jobs are batched together for delivery to a station. From the perspective of individual jobs, there is variation in their arrival times. In particular, $c_a^2=k-1$ 

* *Wait to match time results when variability causes the fabrication lines to deliver product to assembly in an unsynchronized fashion*.

## Effects
* **The Fundamental Law of Variability** - *Increasing variability always degrades the performance of a production system*
	* **Variability Placement** - in a line where releases are independent of completions, variability early in a routing increases cycle time more than equivalent variability later in the routing. 
	* *Variability cascades throughout the line*.  Highly variable outputs from one workstation become highly variable inputs in another (see Flow variability above)
	* *This system is more applicable for push rather than pull systems.*

* **The Law of Variable Buffering** Increasing variability impacts the system along three dimensions *inventory, capacity, and time (either lead time / poor service or cycle time)*. Another way to say this is that variability is buffered by some combination of these dimensions. *If variability is not reduced one way, performance is compromised in other ways*
	* **Buffer Flexibility** pertains to buffers that can be used in more than one way. It reduces the amount of variability buffering required in a production system (i.e., cross trained workers that can cover capacity and time).


* *The greater the variability in effective process times, the greater the average queue of jobs formed and the longer the cycle time.* This effect is apparent when it takes longer to clear the queue resulting from downtimes than for another downtime to occur.
	* All other things equal, long repair times induce more variability than shorter ones
	* Provided availabilities are the same, it is better to have frequent but short outages than infrequent but longer ones. Of course, it is best to have no failures entirely.

* We can use [[Queueing Theory]] to analyze the effects of wait times and variability
	* *Cycle time is often just waiting time*. 

* When variability and utilization are the same, a station with parallel machines will outperform one with dedicated machines. 
* We can also consider the case of buffering on the system using queueing theory
	* In this case, if we interpret the system as two machines in series, where the first machine never starves and the second machine is never blocked, then we observe behavior similar to a M/M/1/b queue where $b=B+2$ and *the extra two buffer spaces are the machines themselves*
	* *The WIP of a M/M/1/b queue is less than that of an M/M/1 queue at the cost of lost throughput. The smaller the buffer, the greater the reduction in throughput*.  
	* The only way to reduce WIP and CT without sacrificing too much throughput is to also reduce variability
	* Finite buffers will force stability regardless of the arrival or service rate, which means WIP cannot blow up. 
	* **Reversibility** means that *throughput is unaffected by the order of the machines on a line*. 

## Mitigation
 * **Variability Pooling** is a technique where we combine multiple sources of variability [^var_pool]
	 * The process times of batches are less variable than the process times of individual parts. The exact relation is given by
	   
	   $$
	   c_0(\text{batch}) = \frac{c_0(\text{individual})}{\sqrt{n}}
	   $$
	* It is better to hold generic inventory that can be used to satisfy demand from multiple sources, because the amount of safety stock (and by extension kept inventory) is reduced. 
	* We can perform queue sharing where WIP that accumulates for a server (machine) is moved to other machines that can accommodate them. Combined queues protect jobs from long failures (i.e., variability in process time)

[^var_pool]: Analogous to [[Financial Market|Diversification]]. 

* A successful variability reduction program can generate capabilities that are transferrable to other parts of the business.
* *The mind-set of variability reduction promotes an environment of continual process capability improvement*

* In an environment with high variability, we will want lead times to be greater than average cycle time to have an acceptable service level. 

* If cycle time variability is low, then we know with a high degree of precision how long it will take a job to get through the plant.
# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 8 - 9
* [[Inventory Management and Control]]
* [[Fundamental Objects in Factory Physics]]
* [[Factory Dynamics]]