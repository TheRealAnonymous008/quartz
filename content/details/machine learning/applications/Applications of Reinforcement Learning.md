# Surveys 
* [^Zhou_2023] Provides a comprehensive survey on the applications of MARL. and some of its challenges
	* This includes the following domains and tasks 
		* *Smart Transportation*- integrating IoT to increase safety, improve transportation efficiency, and reduce environmental impacts 
			* Traffic light control, especially in the global traffic network level 
			* Auto driving, especially with many drivers 
		* *Unmanned Aerial Vehicles*
			* Cluster Control - controlling UAVs to navigate an environment without hitting each other 
			* Environment Monitoring - using UAVs to achieve complete coverage while minimizing overlapping FOVs
			* Collaborative Transportation - using UAVs for a logistics network and making it operate more efficiently 
		* *Intelligent Information Systems*
			* Natural Language Processing- includes RLHF and MARL-powered chatbots that can simulate conversations 
			* Programming Generation - MARL can be used to collaboratively generate, optimize, and test programs 
			* Recommender systems - MARL can be used to enhance collaborative effort, regulate competing parties, and simulating user preferences. 
		* *Public Health and Intelligent Medical Diagnosis* - aims to improve various fields in healthcare including 
			* Disease prediction, diagnosis, and treatment. MARL is good in this context because it can handle collaborative tasks. 
			* Medical image processing via an ensemble of MARL agents.
		* *Smart [[Manufacturing]]* - using AI to optimize the production process. These methods typically require value decomposition to counteract combinatorial action space explosion.
			* [[Factory Optimization Techniques|Job shop]] [[Scheduling Problem|scheduling]] - involves resource allocation, task management and scheduling, especially in a dynamic environment. 
			* Industrial robots - focuses on the level of robots that make products. Also focuses on making these robots. 
			* Preventive maintenance - accounting for machine failure. 
		* *Financial trading* - can simulate both collaboration and competition among agents 
			* Portfolio management - optimize asset allocations and improve returns. 
			* Trading strategy optimization - especially for more complex financial markets
			* Risk Management - MARL systems that can offer decision support, manage prices, test reward formulations
		* *Network Security* 
			* Intrusion detection - MARL can exploit collaborative and communicative agents to detect complex attacks on dynamic networks 
			* Resource optimization - MARL agents that manage resources according to changing network demands. 
		* *Smart Education* - MARL can offer individualized learning experiences, collaborative learning amongst students, and feedback for the teachers 
		* *Science* - general applications in the natural sciences including simulation, discovery, and control. 
	* The paper argues that MARL should be assessed based on moral constraints of human society especially considering the limitations of the approach. 

	[^Zhou_2023]: Zhou, Liu, and Tang (2023) [Multi-Agent Reinforcement Learning: Methods, Applications, Visionary Prospects, and Challenges](https://arxiv.org/pdf/2305.10091.pdf)

* [^Queralta_2020] gives a survey for multi-robot search and rescue systems. 
	* Typical agents in SAR include
		* UAVs - Unmanned Aerial Vehicles. Typically characterized by cameras as sensors due to their size and weight. 
		* UGVs - Unmanned Ground Vehicles. Typically characterized with dexterous manipulation capabilities and robust against uneven terrain
		* USV - Unmanned Surface Vehicles. They operate on the water's surface.
		* UUV - Unmanned Underwater Vehicle. They operate underwater. 
	* *Interoperability is one challenge in SAR robotics* where different types of agents coordinate with each other.
	* Common environments for SAR can be divided into three: Maritime, Urban, and Wilderness.
	* Common challenges for multi-agent SAR include
		* Visual detection especially over vast areas of search or low visibility settings.
		* Long distance operation
		* [[Agent Loocalization|Localization]] / SLAM considering unknown, unstructured environments
		* Establishing long-term communication, and transmitting messages over potentially long distances.
		* Large search areas.
		* Navigation over uneven or unforgiving terrain.
	* Some avenues for research include:
		* Victim identification, Human condition awareness and triage protocols
		* Human-Swarm Interaction and Collaboration
		* Multi-Agent Coordination, including task allocation, path planning, area coverage, exploration, and general planning (both in a centralized and decentralized manner)
		* Online Learning
		* Multi-Objective, Multi-Agent optimization.
		* Agent Perception (see [[Computer Vision]]). 
		* Making solutions less computationally heavy.
		* [[Multimodal Models|Multimodal]] Information fusion
		* **Active Perception** - agents develop an understanding of "why" it senses, chooses "what" to perceive, and then "how, when and where" (see [[Belief-Desire-Intention|an analogous system]])
		* Shared Autonomy
		* Closing the gap between simulations and reality.
		* Heterogeneous swarms that are
			* Interoperable -- different kinds of robots can coordinate with each other
			* Ad hoc -- the types of robots are not predefined
			* Situationally aware -- agents are aware of the variety of robots being used. 


[^Queralta_2020]: Queralta et al. (2020) [Collaborative Multi-Robot Search and Rescue: Planning, Coordination, Perception, and Active Vision](https://ieeexplore.ieee.org/document/9220149?denied=)



# Modeling
* [^Yao_2024] proposes a simulation framework using a small group of representative RL agents for the context of a double auction stock market (agents buy and sell simultaneously)
	* The framework runs all agents simultaneously. Also, all agents are heterogeneous.
	* The paper provides a framework for analyzing whether or not simulations match real world markets by examining statistical characteristics and market responsiveness. 
	* Testing is done with three groups of agents -- (A) agents that continue training throughout the simulation; (B) - agents pre-trained and are used in the simulation without training ; (C) - untrained agents. 
	* *Continual learning RL agents produce the most realistic market simulation and can adapt to changing market conditions*.
	* *Limitations*: Does not address how to calibrate the system.

[^Yao_2024]: Yao, Li, Thomas, and Florescu (2024) [Reinforcement Learning in Agent-Based Market Simulation: Unveiling Realistic Stylized Facts and Behavior](https://arxiv.org/abs/2403.19781)

* [^brusatin_2024] proposes **R-MABM** a rational Macroeconomic ABM to study the impact of rationality in the economy. 
	* *Rationale*: Traditional ABM models do not account for heterogeneity, bounded rationality or nonequilibrium dynamics. RL can overcome these limitations and at the same time alleviate the burden of designing rules for the agents. 
	* Like other [[Computational Macroeconomics|MABMs]], agents (specifically firm agents) have access to  price deltas and firm stock values. They then set price and production quantities. The reward is based on agent profit.
	* We make use of curriculum learning where we gradually introduce RL agents into the environment.
	* *RL agents choose and adapt their strategy according to the level of market competition and rationality*. They can outperform the profits of bounded rational firms.  In particular, RL agents have learn the following strategies in the case of shared policies
		* **Market Power Strategy** - when competition is low, RRL agents learn to charge any desired price on goods sold. They establish [[Competition between Firms|monopolies and oligopolies]].
		* **Dumping Strategy** - when competition is high, RL agents learn to drop the retail price below market level to undercut the competition.
		* **Perfect Competition** - when competition is high and there are a lot of RL agents, the RL agents learn to set quantities and prices in line with the market. 
	* RL agents with independent policies outperform RL agents with shared policies since they can adapt to the market and exploit their own niche.
	* The impact of rationality is as follows:
		* Increased rationality implies higher output.
		* Increased rationality implies higher economic stability under conditions where there is perfect competition.
		* Perfect competition gives highest output and is most responsive. 

![[R-MABM.png]]
<figcaption> R-MABM. Image taken from Brusatin et al. (2024) </figcaption>


[^Brusatin_2024]: Brusatin et al. (2024) [Simulating the economic impact of rationality through reinforcement learning and agent-based modelling](https://arxiv.org/html/2405.02161v1#S2)


* [^ardon_2022] propose an [[Agent Based Modeling|ABM]] network that is compatible with the use of [[Multi-Agent Reinforcement Learning|MARL]] .  The framework encodes the following
	* Partial Observability. 
	* A network model for inter-agent relationships.  Connectivity can either be static or stochastic. 
	* Agent [[Utility|utility functions]] encapsulated as [[Game Theory - Games|types]].
	* Heterogeneous Agent Preferences
	* Support for complex turn orders (i.e., turns based on types)

[^Ardon_2022]: Ardon et al. (2023) [An RL driven multi-agent framework to model complex systems](https://arxiv.org/pdf/2210.06012)

* [^Li_2022] introduces an ABM model augmented with RL that simulates the Schelling Segregation model. 
	* *Result*: High moving expenses promote social segregation despite tolerance to heterogeneous neighbors.

[^Li_2022]: Li (2022) [The impact of moving expenses on social segregation: a simulation with RL and ABM](https://arxiv.org/abs/2211.12475)


* [^Kwak_2021] Applies reinforcement learning in the context of public health -- particularly handling pandemics. It aims to optimize lockdown and travel restriction policies and the timing of enacting these policies. 
	* Real world country and territory population data was used alongside COVID-19 epidemiological data. 
	* Algorithm recommends (unsurprising) strategy of early lockdowns and travel bans and loosening these restrictions later on in the pandemic to balance economic costs. 
	* Models the entirety of society as a high level construct due to data limitations. 

	[^Kwak_2021]: Kwak, Ling, and Hui (2021): [Deep reinforcement learning approaches for global public health strategies for COVID-19 pandemic](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0251550)

* [^Ardon_2021] presents a financial framework for replicating complex market conditions involving two agent types -- Liquidity providers and Liquidity takers via MARL.
	* Liquidity Providers continuously quote buy and sell prices at which they are willing to take.
	  
	  Liquid Takers are the consumers who execute orders.
	  
	  A third agent -- an electronic communication network (ECN) decides which LPs trade with which LT. The ECN exposes prices on both bid and ask sides.
	* LPs maintain an inventory of the quantity traded until an investor accepts the trade.
	* The MARL approach is shared across agent types. The shared policy is studied to gather insights
[^Ardon_2021]: Ardon et al. (2021) [Towards a fully RL-based Market Simulator](https://arxiv.org/abs/2110.06829)


* [^Sert_2020] combines reinforcement learning techniques with ABM techniques to study the dynamics of segregation. 
	* *Contribution*: Combining MARL and ABM to create an artificial environment to observe potential and existing behaviors associated to rules of interactions and rewards.  
	* In particular, the rewards each agent receives constitutes the following:
		* *Segregation reward* to promote segregation. 
		* *Interdependence reward* to promote interactions among agents of a different kind. 
		* *Vigilance reward* to promote the agent staying alive. Added to incentivize the agent to stay alive to collect more rewards.
		* *Death reward* to punish agents who lose to interactions against agents of the opposite kind. 
		* *Occlusion reward* to punish agents moving to an area occupied by agents of the same kind. 
		* *Stillness reward* to punish agents for staying still. 
	* Spatial segregation diminishes as more interdependencies among agents of different kinds are added in the same fashion as if agents are tolerant to one another
	* Older agents tend to be more segregated than younger agents. 


	[^Sert_2020]: Sert, Bar-Yam, and Morales (2020). [Segregation dynamics with reinforcement learning and agent based modeling](https://www.nature.com/articles/s41598-020-68447-8)

# Policy-Making
* [^Waseem_2024] present a MARL approach for Flexible Manufacturing systems that can process multiple product types. 
	* The paper addresses the problem of scheduling when the environment complexity increases and when product types require distinctive workflows.
	* The paper proposes a combination of [[Static Games of Complete Information|Game Theoretic]] and MARL-based approaches 
		* A Nash game handles the interactions between robots to design collaboration cost functions.
		* A MADDPG system determines the actions of each agent. 
		* The overall action of each agent is dependent on the strategy chosen in the Nash game and by the MADDPG policy. 

[^Waseem_2024]: Waseem and Chang (2024) [From Nash Q-learning to nash-MADDPG: Advancements in multiagent control for multiproduct flexible manufacturing systems](https://www.sciencedirect.com/science/article/pii/S0278612524000530)


* [^kaven_2024] proposes a MARL-based approach for Lineless Mobile Assembly Systems.
	* The paper addresses the following related problems
		* The layout problem (since Mobile Assembly systems have a flexible factory layout). The goal is to determine the layout plan and minimize the cost of rearranging facilities.
		*  Job shop [[Scheduling Problem]]. In particular, the Flexible Job Shop Problem. 
	* The control approach used is an asynchronous, cooperative, [[Heterogeneous MARL|heterogeneous]] MARL
		* The control algorithm determines the placement of stations (coordinates of the station in the environment) and the scheduling of jobs
		* The Discrete Event Simulator requests decisions from the RL algorithm. 
			* The layout planner solves the layout problem by computing the placement of each station per decision step, given the state vector (as encoded by the encoder)
			* The scheduling agent solves the flexible job shop problem. The agent computes the next station, process pairing for each job.
	* The paper uses Multi agent PPO.


[^Kaven_2024]: Kaven et al. [Multi agent reinforcement learning for online layout planning and scheduling in flexible assembly systems](https://link.springer.com/article/10.1007/s10845-023-02309-8)

* [^Zhang_He_2023] proposes using MARL for industrial applications, in particular for flexible job scheduling
	* *Contribution*: Integrating MARL with Deep RL techniques to handle the larger search space via decentralized execution and more parameters. MARL also allows the agents to operate in a cooperative setting.
	* It operates on the flexible job shop scheduling task wherein 
		* *Procedure constraint*: Each job operation is to be processed in a given order
		* *Exclusion constraint*: Each machine can only process one operation for a job at any time 
		* *Constant constraint*: There is a constant set of machines for each operation of jobs. 
		* A schedule is a valid sequence that assigns operations of jobs to specific machines at the appropriate time slots subject to the above constraints.
		* The agent must also perform *job routing* to satisfy the constant constraint among the set of machines that can perform an operation. 
	* It makes use of a *multi-agent graph* with agents as nodes and edges based on the order of machines processing the operations of jobs, and the possible operations of jobs that can be processed. Here, *each agent cooperates with their neighbors on the graph*. 
	* The specifications for the environment are as follows:
		* *The environment consists of a set of machines and a set of jobs* in which jobs are routed to specific machines and sequentially processed subject to the constraints of FJSS 
		* *Each machine is associated with an agent for job sequencing* -- it can select the next job from the machine's job candidate set to be processed when available. 
		* *Each job is associated with an agent for job routing* -- it can choose the next machine to process its next operation when the current operation is finished, in which case it is added as a job candidate for the next machine. 
		* Each job has a workload quantity (indicating how much work per operation); Each machine has a productivity quantity (indicating how much work per step)
		* The environment is partially observable
		* *All actions are triggered only when a machine is available or the job's current operation is finished at the current time step*
		* *Agents are penalized for taking too long*. The goal is to minimize the production time. 
	* *DeepMAG is defined as follows*
		* A forward pass constitutes the following state 
			* Update the multi-agent graph 
			* Update features of each agent. 
				* *For machine-centric features* -- The feature vector encodes information about the productivity, number of waiting, routed, and executing tasks, current workload quantity of the machine. It also considers aggregates (sums) across each relationship set (see below)
				* *For job-centric features* -- The feature vector consists of information about the number of machines related to it, as well as the sum, maximum, and minimum of all workload quantities in jobs that are in a relationship set with it (see below)
			* Update the first DQN for job routing.
			* Update a second DQN for job sequencing 
		* The MAG specifies relationships between agents (both machines and jobs)
			* *Static relationships* are between machines in terms of consecutive operations. There are four types of this relationship 
				* Machine $m$ may send to machine $m'$. $m$ is a *parent* of $m'$
				* Machine $m$ may receive jobs from machine $m'$. $m'$ is a *child* of $m$
				* Machine $m$ and $m'$ have a common child. $m$ and $m'$ are *couples*. They are competitive on the resources of their common children 
				* Machine $m$ and $m'$ have at least one  common parent. $m$ and $m'$ are *siblings*. They are cooperative on the resources of their common parent. 
			* *Executing relationships* are between jobs and machines indicating a job is executing at the machine 
			* *Routing relationships* are between jobs and machines, indicating the job has just finished their operation and is ready for routing for their next operation 
				* The routing job set consists of all jobs with a *common routing machines*. They are competitive on the common routing machine.
				* The *ancestor set* consists of all jobs $j'$ with a path to job $j$. 
			* *Waiting relationships* are between jobs and machines indicating that the job is in the machine's waiting queue.
		* Two DQNs are used to reduce cost and enable scalability 
	* The following key results were found 
		* When compared to methods that simply rely on heuristics, DeepMAG always achieves best performance  regardless of the number of jobs.
		* The size of the replay buffer should be just right (not too small and not too big to contain outdated data). 
		* An appropriate number of target network updates is needed (not too few to be too outdated and not too many to be unstable )
		* An appropriate number of neurons is necessary (not too few to underfit and not too many to overfit or be too slow to compute)
	* *Limitations*: The paper does not consider a dynamic setting (i.e., when job requirements change). 

	![[DeepMAG.png|500]]
	<figcaption> DeepMAG. Image Taken from Zhang, He, Chan, and Chow (2023) </figcaption>

	[^Zhang_He_2023]: Zhang, He, Chan, and Chow (2023) [DeepMAG : Deep reinforcement learning with multi-agent graphs for flexible job shop scheduling](https://www.sciencedirect.com/science/article/abs/pii/S0950705122011790?via%3Dihub)

* [^Koster_2022] builds a democratic AI that can design a social mechanism that humans would prefer by majority. It aims for value-aligned policy innovation 
	* *Rationale*: Designing a mechanism that addresses income inequality and prevents free riding is difficult. 
	* *Contribution*: it is possible to harness for value alignment the same democratic tools for achieving consensus that humans use in society.  *AI can be trained to satisfy a democratic objective* 
	* A deep RL agent is designed to redistribute funds back to players under both wealth equality and inequality. It, along with other baseline policies, were voted by human players. 
	* Policies are represented using the *ideological manifold* by considering the fractional payout each player receives. It is specified by parameter $v$ which mixes between absolute and relative payouts. 
		* The absolute component combines their contribution with the average from that of other players 
		* The relative component is determined by the ratio of contribution to endowment. 
	* The paper suggests that a simple mechanism (such as this operating in only two dimensions) is *perceived as transparent and understandable* to humans. 
		* The agent preserves privacy by operating on the distributions rather than on the individuals themselves. *It is slot equivariant*.
	* *Limitations*: A democratic approach is not necessarily the best approach since it might lead to the "tyranny of the majority". A proposed solution by the paper is to augment the cost function to protect minorities.  


	[^Koster_2022]: Koster et al. (2022) [Human-centred mechanism design with Democratic AI](https://www.nature.com/articles/s41562-022-01383-x)


* [^Klar_2021] Applies reinforcement learning for automated layout, and in particular making use of DDQL in order to layout units for a factory. Presents more as a proof of concept. 

	[^Klar_2021]: Klar, Glatt, and Aurich (2021) [An implementation of a reinforcement learning based algorithm for factory layout planning](https://www.sciencedirect.com/science/article/pii/S2213846321000651) 


* [^Guo_2021] explores an online learning mechanism to learn an [[Game Theory|equilibrium]] for resource allocation within exchange [[Microeconomics|economies]].
	* Rather than rely on modeling the agents' utilities, we instead make use of feedback from the environment. The goal is Pareto-efficiency. 
	* The problem is defined as follows. Assume we have  $n$ agents and $m$ divisible resources. We initialize an endowment for each agent $e_i=\set{e_{i1},\dots ,e_{im}}$.  For simplicity and WLOG, assume that for each resource $j$
	  $$
	  \sum_{i}e_{ij} = 1
	  $$
	  So that the resource space can be denoted $[0,1]^m$. 
	  
	  An allocation $x=(x_1,\dots,x_n)$, $x_i\in[0,1]^m$ and $x_{ij}$ denotes the amount of resource $j$ allocated to agent $i$.  The set of feasible allocations is denoted
	  $$
	  \mathcal{X} =\set{x \mid \sum_{i=1}^m x_{ij} \le 1, \forall i, j: x_{ij} \ge 0 }
	  $$
	  An agent's utility $u_i:[0,1]^m\to [0,1]$ determines the valuation for allocation $x_i$. We also assume that $u_i$ is non-decreasing since more allocations do not hurt.
	  $$
	  \forall x_i \le x_i', u_i(x_i)\le u_i(x_i')
	  $$
	  A price vector $p, p\in \mathbb{R}^{+m}$, $1^Tp=1$ (to make sure all prices are normalized since only relative prices matter), is defined for the exchange economy. $p_j$ denotes the price  for resource $j$.
	  
	  Thus, each agent has a price budget $p^Te$.
	  
	  The goal of each agent is to maximize the utility under the budget. That is, for the entire system, we find the demand under equilibrium
	  $$
	  d_i (p) = \underset{x_i\in[0,1]^m}{\text{argmax}}  \ u_i(x_i) \ \ \ \ \ \text{subject to } p^Tx_i \le p^T e_i
	  $$
	* To allocate resources, we set the prices for the resources and have agents maximize utility under this price system. 
	  
	  We seek the [[Microeconomics|Walrasian equilibrium]] in the context of fair division.
	  
	  Under fair division, we require the following
		* Allocations have **sharing incentive** -- $u_i(x_i)\ge u_i(e_i)$.  Each agent has an incentive to share because doing so may yield greater utility.
		* Allocations are **Pareto Efficient** -- the utility of one agent can be increased if another agent's utility decreases.  That is, if there is no $x'$ where $u_i(x_i ) \ge u_j(x_i') \ \forall i$ and there exists no $i$ where $u_i(x_i)>u_i(x_i')$. The set of all $x'$ that are Pareto Efficient is denoted $\mathcal{PE}$
	* To make the setting not require a priori knowledge of the utilities, we frame the problem further as follows.
	  
	  Each agent reports feedback for a given time step $\set{y_i^t}$ where $y_i^t$ is sub-Gaussian and 
	  $$
	  \mathbb{E}[y_i^{t+1} \mid x_i^t] = u_i(x_i^t)
	  $$
	  We optimize two varieties of losses.

		* The CE loss $L_T^{\text{CE}}$ is the difference of the utility between current allocation and the CE equilibrium. Denote $x^+=\max(0,x)$
		  $$
		  \begin{split}
		  l^{\text{CE}} (x,p) &= \sum_{i=1}^n \left(\max_{x_i' : \ \ p^Tx_i' \le p^Te_i} u_i(x_i') - u_i(x) \right)^+ \\
		  L_T^\text{CE} &= \sum_{t=1}^T l^{\text{CE}} (x_t, p_t) 
		  \end{split} 
		  $$
		* The SI loss is defined with fair allocation in mind, defined as follows
		  $$
		  \begin{split}
		  l^{\text{SI}} (x) &= \sum_{i=1}^n (u_i(e_i) - u_i(x_i))^+ \\
		  l^{\text{PE}} &= \inf_{x'\in\mathcal{PE}} \sum_{i=1}^n (u_i(x_i')-u_i(x_i))^+ \\
		  l^{\text{FD} (x)} &= \max(l^{\text{PE}}(x), l^{\text{SI}}(x)) \\
		  L_T^\text{FD} &= \sum_{t=1}^T l^\text{FD}(x_t)
		  \end{split}
		  $$
	* We make additional assumptions. Let $\phi_j : [0,1]\to[0,1]$ be an increasing function mapping $x_{ij}$ to a feature value; $\mu: \mathbb{R}^+\to [0,1]$ be an increasing function, and $\Theta \subset \mathbb{R}^{+m}$ be a set of positive parameters. Then we consider utilities in the following class
	  $$
	  \mathcal{P} = \set{\set{u_i}_{i=1}^n ; \ \ u_i(x_i ) =\mu(\theta_i^T\phi(x_i)  \ \text{for some } \theta_i \in \Theta, \forall i}
	  $$
	  We aim to learn $\theta_i^\ast \in \Theta$. We relax these assumptions further for the sake of practical use
		* $\mu$ is continuously differentiable. It is Lipschitz-continuous with constant $L_\mu$ and $C_\mu= \inf_{\theta\in \Theta, x\in \mathcal{X}} \dot\mu (\theta^T\phi(x)) > 0$
		* $\Theta\subset [\theta_{\text{min}},\infty)^m$, $\theta_\text{min} >0$. 
	* For the algorithm, we define 
	  $$
	  \begin{split}
	  \alpha_t^2 &= 4\frac{\kappa^2 \sigma^2}{C_\mu^2} m\log(t) \log\left(\frac{m}\delta_k{}\right) \\
	  \kappa &= 3+ 2\log(1+2 \| \phi(1)\|_2^2)
	  \end{split} 
	  $$
	* We can prove the following bounds for the loss under the relaxed conditions above. Both show that learning is done at $\sqrt T$ rate. 
		* (*[^Guo_2021] Thm 4.1*) Let $\delta>0$. Choose $\delta_t = \frac{2\delta}{n\pi^2 t^2}$. The following upper bounds hold with probability $1-\delta$ 
		  $$
		  L^{\text{FD}}(T), L^\text{CE}(T) = O\left(n\left(m+\frac{m^2}{\sqrt M}\right) \sqrt T (\log(nT/ \delta) + \log(T))\right) 
		  $$

		* (*[^Guo_2021] Thm 4.2*) Let $T>M\max(m^2,n)$. Choose $\delta_t = \frac{1}{T}$. Then the following upper bounds hold 
		  $$
		  \mathbb{E}[L^{\text{FD}}(T)] , \mathbb{E}[L^{\text{CE}}(T)] \in O\left(n\left(m + \frac{m^2}{\sqrt M}\right) \sqrt T (\log(T))\right)
		  $$


![[Learning EEs via Bandits.png]]
<figcaption> Online Learning for Competitive Equilibria. Image taken from Guo et al. (2021) </figcaption>

[^Guo_2021]: Guo et al. (2021) [Learning Competitive Equilibria in Exchange Economies with Bandit Feedback](https://arxiv.org/abs/2106.06616)



* [^Wen_2021] proposes **MARL framework for Auto-Bidding (MAAB)** which learns auto-bidding strategies in a multi-agent setting.  It also examines the use of a [[Mean Field MARL|Mean field approach]] for scale. 
	* *Motivation*: Prior approaches focused only on an Independent-Learning setting where agents ignore the presence of others. 
	  
	  The goal here is to formulate the problem as a cooperative, competitive scenario between individual agents. 
	* The problem is as follows. The agents have $T$ impression opportunities and can give a bid $b_i^t$ on behalf of advertiser $i$ at time $t$. The agents play a  [[Auction Theory|closed second-price auction]] , where if agent $i$ wins they receive impression value (interpreted as reward)  $v_i^t$ and makes payment $p^t$. Each agent also has a budget constraint $B_i$. The goal is 
	  
	 $$
	  \begin{split}
	  \text{maximize } & \ \ \ \ \ \sum_{t=1}^T v_i^t x_i^t \\  
	  \text{subject to} & \ \ \ \ \ \sum_{t=1}^T p^t x_i^t \le B_i
	  & \ \ \ \ \
	  \end{split}
	  $$
	  Where $x_i^t\in \set{0,1}$ denotes whether advertiser $i$ wins impression at $t$.
	  
	  The policy of the agent outputs the bid price. That is
	  $$
	  \begin{split}
	  b_i^t &= \pi_i(o_i^t) \\
	  o_i^t &= (B_i^t, v_i^t, T-t)
	  \end{split}
	  $$
	  Where $B_i^t$ is the remaining budget (clamped at $0$). 
	* In a full competition setting, the above causes a [[Competition between Firms|Monopoly]] to emerge. In a full cooperative setting, the social welfare is much higher but each agent has a lower profit. 
		* To balance both, we introduce a weighting parameter $a_i$ that weighs each agent's contribution to the total reward (i.e., the social welfare) $r^{\text{tot}}$ Where
		  $$
		  \begin{split}
		  r_i&=z_ i \ a_tr^{\text{tot}} \\
		  a_i &= \frac{\exp(b_i/\tau)}{\sum_j \exp(b_j/\tau)}
		  \end{split}
		  $$
		  The temperature $\tau$ regulates the trade off between competition and cooperation.
		  $z_i$ is an indicator variable that is $1$ when the bid exceeds the bar set and $0$ otherwise (see below for a description) 
		  
		* (*[^Wen_2021] 4.1*) In the two agent bidding cases  where $v_1>v_2$, and $b_1,b_2\in [b_{\text{min}}, b_{\text{max}}]$ In the case where either $v_1\ge 2v_2$ or when $v_1 < 2v_2$ but 
		  $$
		  \tau \ge \frac{\log(2v_2/v_1 - 1)}{b_{\text{min}} - b_{\text{max}}}
		  $$
		  Then $b_1\ge b_2$ and the relation is cooperative. Otherwise, competitive. 
	* To prevent agents from harming the platform's revenue, we *introduce bar agents during training (not during execution)*. A bar agent introduces a bidding bar for their corresponding agent. 
	  
	  The bar agents are rewarded with the reward
	  $$
	  \bar r_i = z_ip
	  $$
	* To scale this, we use the mean-field setting. In this setting, we group individual agents based on their advertiser's objective. 
	  
	  In the mean field case, we consider for each group the mean field policy that outputs the mean value and budget. The bid is derived based on the advantage over the mean value.

![[MAAB.png]]
<figcaption> MAAB. Image taken from Wen et al. (2021) </figcaption>

![[Mean Field MAAB.png]]
<figcaption> Mean MAAB. Image taken from Wen et al. (2021)  </figcaption>

[^Wen_2021]: Wen et al. (2021) [A Cooperative-Competitive Multi-Agent Framework for Auto-bidding in Online Advertising](https://arxiv.org/abs/2106.06224)

* [^kim_2020] proposes a flexible smart [[Manufacturing|manufacturing system]] with distributed intelligence
	* Unlike previous work, it aims to decentralize the decision making process for planning and scheduling. It also aims to make RL agents be more adaptive and flexible when responding to a dynamic manufacturing environment.
	* Consists of three agents 
		* The **enterprise layer** interfaces with the customer directly, receives customer orders and delivers the job schedule information to the customer.
		* The **cloud layer** stores customer order information and production plan and scheduling regarding the agent. It also provides the simulation environment.
		* The **machine layer** is responsible for the decision making between intelligent agents.
	* The manufacturing pipeline is as follows
		* Job arrives and its information is uploaded. New jobs are produced.
		* Job evaluation, scheduling, and prioritization.
		* Machines take jobs. If the job can be negotiated for, then machines negotiate between the jobs.
			* The goal is to balance between the setup time of having many agents take a job, and the throughput increase of having many agents take the job.
		* Job evaluation and negotiation is repeated until all jobs are allocated.
		* Use the RL policy to make next decisions
		* Execute the production plan

![[Smart Manufacturing MARL architecture.png]]
<figcaption> Smart Manufacturing Architecture. Image taken from Kim et al. (2022) </figcaption>

![[Smart Manufacturing MARL pipeline.png]]
<figcaption> Smart Manufacturing Sequential Pipeline. Image taken from Kim et al. (2022) </figcaption>

[^Kim_2020]: Kim et al. (2020) [Multi Agent System and Reinforcement Learning Approach for distributed intelligence in a flexible smart manufacturing system](https://www.sciencedirect.com/science/article/abs/pii/S0278612520301916)



* [^Zheng_Trott_2020] examines the use of MARL to develop a tax system that promotes and balances equality and productivity. It is effective in simulations with human participants and can be extended to real economies. 
	* *Rationale*: 
		* Economic models are too simplistic and do not capture the complexities of humans. 
		* Prior methods for mechanism design did not consider agents that learnt how to behave .Agents were assumed to be static. 
		* It is also hard to test economic policy since it can deal with long time scales. 
	* Both the workers in the economy and the policy maker are powered by reinforcement learning.  
		* In the model, higher skilled workers earn more for building houses. Building houses takes effort which lowers [[Utility|utility]]. 
		* To quantify equality, the Gini Index is used as follows 
		  
		  $$
		  \text{eq}(x) = 1- \text{gini} (x)\frac{N}{N-1}
		  $$
		* To quantify productivity, the sum of the agent's wealth is used
		* The policy maker sets the tax rates. 
	* Learning is done via an inner-outer loop. The policy maker has no prior economic knowledge or assumptions on agent's utility functions. 
		* The inner loop optimizes the agents. The outer loop optimizes the social planner. 
		* As is typical of MARL, there is more non-stationarity due to changing strategies.
		* *Note that both agents and the central planner are trained jointly*.
		* Agents are first pre-trained on the free market scenario to adapt to the game's dynamics. Then, a baseline (non AI economist) tax policy is applied.
		* It makes use of *entropy regularization*. 

	![[AI Economist Pseudocode.png]]
	<figcaption> AI Economist Pseudocode. Image taken from Zheng et al. (2020)</figcaption>

	* *Consequences observed*
		* *Specialization comes because workers learn to balance income and effort*.
			* Agents with lower skill earn income by collecting and selling raw materials  
			* Agents with higher skill earn income by building products and buying from low skill agents. 
		* *The AI policy maker achieves a better trade-off between equality and productivity than baseline methods*.
			* Under the AI economist, lower income workers have lower tax burden
			* The worker agents learn to game the system by alternating between their types] based from whether they are high skilled or low skilled.
		* *AI and human behavior differs substantially*. Humans display a higher frequency of adversarial behavior 
	* *Limitations*
		* They do not model the behavioral aspect of economics and the interactions between people 
		* The simulation is relatively small, operating only on a small gridworld and using only a single quantifier for "skill" without considering additional possible social roles. 


	![[AI Economist Framework.png]]

	<figcaption> The AI Economist framework. Image taken from https://blog.salesforceairesearch.com/the-ai-economist  </figcaption>

	![[AI Economist Agent Architecture.png]]
	<figcaption> AI Economist Agent Architecture. Image taken from Zheng et al. (2020) </figcaption>

	[^Zheng_Trott_2020]: Zheng et al. (2020) [The AI Economist: Improving Equality and Productivity with AI-Driven Tax Policies](https://arxiv.org/pdf/2004.13332.pdf) . Supplemental [blog](https://blog.salesforceairesearch.com/the-ai-economist/)
# Links 
* [[Reinforcement Learning]]
	* [[Off Policy Prediction and Control with Approximation]]
	* [[Policy Gradient Methods]]
* [[Multi-Agent Reinforcement Learning]]
	* [[MARL Problem Statement]] 
	* [[MARL Deep Learning]]
	* [[Self Play]]
* [[Natural Language Processing]]
* [[Agent Based Modeling]]

* [[Dynamic Games of Incomplete Information]]
* [[Mechanism Design]]
* [[Economics]]