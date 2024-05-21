* **Queueing theory** studies waiting lines or queues under the assumption of known queue lengths and waiting time distribution
* A **queue** consists of jobs that arrive to the queue, possibly wait some time, take some time to be processed, and then depart from the queue. 
	* The queue may consist of servers that take an arriving job, process it, and when the job departs, is free to take new jobs. 

* Single queueing nodes are described using **Kendall's Notation** of the form $A/S/c/K/N/D$ where
	* $A$ describes the distribution of durations between each arrival to the queue
	* $S$ describes the service times for jobs
	* $c$ describes the servers at the node. 
	* $K$ (optional) describes the capacity of the queue
	* $N$ (optional) describes the size of the population of the jobs to be served
	* $D$ (optional) describes the queueing discipline.

# Fundamental Relations
* We denote the average arrival rate as $\lambda$ and the average service rate as $\mu$
* The average service time is denoted $\tau = \frac{1}{\mu}$
* The **Utilization** $\rho$ is given by  
  $$
  \rho=\frac{\lambda}{\mu}
  $$

* The expected total wait time is the sum of the average service time and the average wait time in the queue
  
  $$
  \mathbb{E}[W] = \mathbb{E}]W_q] + \mu
  $$

* **Little's Law** states that the long term average number $L$ of jobs (i.e., WIP) in a stationary system is equal to the long term average effective arrival rate (i.e., throughput) $T$ times the average time $W$ a customer spends in a system (i.e., cycle time)
  
  $$
  L = T W
  $$

* When the queue has infinite capacity, $T=\lambda$ because what goes in must come out 
* When the queue has finite capacity, $\lambda$ instead denotes the rate of potential arrivals as if the system were not full. In a similar vein,  $\rho$ is the utilization assuming no arrivals were turned away.
# Queueing Systems
## M/M/1
* Both arrival and service rates are characterized with an exponential distribution resulting in the Markov property. These can be modelled with a Poisson process with means $\lambda$ and $\mu$ respectively. 
* The state of the system is characterized with the number of jobs in queue, denoted $n$.

* The dynamics of the system is governed by the following recurrence relation of differential equations
  
  $$
  \begin{split}
  p_k'(t) &= -(\lambda + \mu)p_k(t) + \mu p_{k+1}(t) + \lambda p_{k-1}(t) \\
  p_0'(t) &= -\lambda p_0(t) + \mu p_1(t) 
  \end{split} 
  $$

* In the long term , we observe that given $\lim_{t\to\infty} p_k(t) = \pi_k$ 
  
  $$
  \begin{split}
  \pi_0 &= 1-\frac{\lambda}{\mu} \\
  \pi_k &= \pi_0 \left(\frac{\lambda}{\mu}\right)^k 
  \end{split}
  $$
	* Intuitively, this means that if the number of arrivals is less than the number of departures on average, the probabilities $\pi_k$ will converge.
	  
	  This only happens when $\lambda < \mu$. 

	* *The number of customers in the system follows a geometric distribution with parameter $1-\rho$.*
	* The average number of jobs  is 
	  $$
	  \frac{\rho}{1-\rho}
	  $$ 
	* Using Little's law, the average response time is given by
	  $$
	  \frac{1}{\mu-\lambda}
	  $$
	* Using Little's law, the average time spent waiting  is given by
	  $$
	  \frac{\rho}{\mu-\lambda}
	  $$
	* The number of jobs in the queue is given by 
	  
	  $$
	  \frac{\rho^2}{1-\rho}
	  $$

## M/G/1 
* The long run average probability that the server is busy is the utilization $\rho$. 
* The average number of jobs in service as seen by a randomly arriving job is also given by the utilization $\rho$ .
* The average remaining process time of a job in service as seen by a randomly arriving job is approximated by 
  
  $$
  u\frac{\rho (c_s^2+1)}{2\mu}
  $$

## G/G/1
* Here we consider the general case of arrival and service time distributions. 
* We can approximate the mean waiting time using the **Kingman Approximation**. 
  
  Denote 
  $c_a$ - the coefficient of variation for arrivals 
  $c_s$ - the coefficient of variation for service times
  
  $$
  \mathbb E[W_q] \approx \left(\frac{c_a^2 + c_s^2}{2}\right)\left(\frac{\rho}{1-\rho}\right) \tau 
  $$
  
  This is also known as the **VUT formula**. Respectively, the terms are the utilization, variability and service time.

* If we denote $W_q(M/M/1)$ as the wait time of an M/M/1 queue, and $W_q(G/G/1)$ for the G/G/1 queue, we observe that the Kingman approximation can be written as 
  
  $$
  \mathbb{E}[W_q(G/G/1)] = \mathbb{E}[W_q(M/M/1)] \left(\frac{c_a^2 + c_s^2}{2}\right)
  $$

* When variability $V>1$, the queue time is greater than the M/M/1 queue. Conversely, when variability $V<1$, the queue time is smaller than the M/M/1 queue

* The expected number of jobs in the system is given by the following approximation
  
  $$
  L \approx \lambda \ (\mathbb{E}[W_q] + \mu) = \left(\frac{c_a^2 + c_s^2}{2}\right)\left(\frac{\rho^2}{1-\rho}\right) + \rho   
  $$



## M/M/c
* An extension of [[#M/M/1]] except we allow for $c$ servers.
* The expected wait time for this queue is given by the following
  
  $$
  \mathbb{E}[W_q] = \frac{\rho^{\sqrt{2(c+1)}-1}}{c(1-\rho)}\frac{1}{\lambda}
  $$

## G/G/c
* In a similar vein to the Kingman approximation, we have the following approximation from Whitt.
  
    $$
  \mathbb{E}[W_q(G/G/c)] = \mathbb{E}[W_q(M/M/c)] \left(\frac{c_a^2 + c_s^2}{2}\right)
  $$
  In closed form this becomes
   $$
  \mathbb E[W_q] \approx \left(\frac{c_a^2 + c_s^2}{2}\right) \frac{\rho^{\sqrt{2(c+1)}-1}}{c(1-\rho)}\frac{1}{\lambda} 
  $$
## M/M/1/b
* A variation of the [[#M/M/1]] queue except the only valid states are $0,\dots,b$. 
* The dynamics of the system is governed by the following recurrence relation of differential equations
  
  $$
  \begin{split}
  p_b'(t) &=  -\mu p_{b}(t) + \lambda p_{b-1}(t)\\
  p_k'(t) &= -(\lambda + \mu)p_k(t) + \mu p_{k+1}(t) + \lambda p_{k-1}(t) \\
  p_0'(t) &= -\lambda p_0(t) + \mu p_1(t) 
  \end{split} 
  $$

* In the long term , we observe that given $\lim_{t\to\infty} p_k(t) = \pi_k$ 
  
  $$
  \begin{split}
  \pi_0 &= \frac{1-\mu}{1-\mu^{b+1}} \\
  \pi_k &= \pi_0 \ \rho^k
  \end{split}
  $$

* We observe the following values for throughput $T$
  
  $$
  T=\begin{cases}
  \frac{1-\rho^b}{1-\rho^{b+1}} \lambda & \rho \ne 1 \\\
  \frac{b}{b+1}\lambda = \frac{b}{b+1}\mu & \rho = 1
  \end{cases}
  $$
  
  Similarly for the number of jobs in total we have
   $$
  L=\begin{cases}
  \frac{\rho}{1-\rho} - \frac{(b+1)\rho^{b+1}}{1-\rho^{b+1}} & \rho \ne 1 \\\
  \frac{b}{2} & \rho = 1
  \end{cases}
  $$

## G/G/1/b
* The general idea for utilization $u \ne 1$ is to use the utilization in the non-blocking case (see [[#G/G/1]]) , say $\rho_{\text{nb}}$ and correct it to obtain $\rho$.
* For $u < 1$, we correct the utilization using
  
  $$
  \rho'=\frac{L_\text{nb} -u}{L_\text{nb}}
  $$
  
  The throughput is then obtained via substitution of $\rho'$
  
  $$
  T \approx\frac{1- u\rho^{b-1}}{1-u^2 \rho ^{b-1}}\lambda
  $$
* For $u > 1$, we can compute $L_\text{nb}$ by reversing the line which is approximately the same as the original. Using the Kingman equation with $1/u$ as the utilization.
  
  $$
  L_\text{nb} \approx \left(\frac{c_a^2 + c_s^2}{2}\right)\left(\frac{1/u^2}{1-1/u}\right) + \frac{1}{u}
  $$
  
  The corrected utilization for the reversed line is also given by
  
  $$
  \rho = \frac{L_\text{nb}}{L_\text{nb} - 1/u}
  $$
  Throughput is then found using substitution of the above $\rho$

* For $u=1$, we use the approximation by Buzacott and Shanthikumar 
  
  $$
  T \approx \frac{c_a^2 + c_s^2 + 2(b-1)}{2(c_a^2 + c_b^2 + b-1)}
  $$

* The values of $L$ and $W$ for this line can be bound as follows. 
	* For small buffers, $L$ will be close to but less than the maximum buffer in the system
	  
	  For large buffers, $L$ approaches the same bound for the G/G/1 queue, so 
	  
	  $$
	  L<\min(L_\text{nb}, b)
	  $$
	* Similarly, from Little's law, $W$ is bound as follows
	  
	  $$
	  W > \frac{\min(L_\text{nb}, b)}T{}
	  $$

# Links
* [[Factory Physics by Hopp and Spearman|Hopp and Spearman]] - Ch. 8 
* [Queueing Theory and the Poisson Process](https://www.youtube.com/watch?v=rBIQmwaoZfs&list=WL&index=1&t=1090s)
* [[Probability]]
* [[Probability Distributions Zoo]]