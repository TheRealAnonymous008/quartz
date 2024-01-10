* [^Sert_2020] combines reinforcement learning techniques with [[Agent Based Modeling|ABM]] technique to study the dynamics of segregation. 
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

* [^Klar_2021] Applies reinforcement learning for automated layout, and in particular making use of DDQL in order to layout units for a factory. Presents more as a proof of concept. 

[^Klar_2021]: Klar, Glatt, and Aurich (2021) [An implementation of a reinforcement learning based algorithm for factory layout planning](https://www.sciencedirect.com/science/article/pii/S2213846321000651) 

* [^Kwak_2021] Applies reinforcement learning in the context of public health -- particularly handling pandemics. It aims to optimize lockdown and travel restriction policies and the timing of enacting these policies. 
	* Real world country and territory population data was used alongside COVID-19 epidemiological data. 
	* Algorithm recommends (unsurprising) strategy of early lockdowns and travel bans and loosening these restrictions later on in the pandemic to balance economic costs. 
	* Models the entirety of society as a high level construct due to data limitations. 

[^Kwak_2021]: Kwak, Ling, and Hui (2021): [Deep reinforcement learning approaches for global public health strategies for COVID-19 pandemic](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0251550)


* [^Zhou_2023] Provides a comprehensive survey on the applications of MARL. and some of its challenges (see [[MARL Problem Statement#Human Interaction|here]]). 
	* This includes the following domains and tasks 
		* *Smart Transportation*- integrating IoT to increase safety, improve transportation efficiency, and reduce environmental impacts 
			* Traffic light control, especially in the global traffic network level 
			* Auto driving, especially with many drivers 
		* *Unmanned Aerial Vehicles*
			* Cluster Control - controlling UAVs to navigate an environment without hitting each other 
			* Environment Monitoring - using UAVs to achieve complete coverage while minimizing overlapping FOVs
			* Collaborative Transportation - using UAVs for a logistics network and making it operate more efficiently 
		* *Intelligent Information Systems*
			* [[Natural Language Processing]] - includes RLHF and MARL-powered chatbots that can simulate conversations 
			* Programming Generation - MARL can be used to collaboratively generate, optimize, and test programs 
			* Recommender systems - MARL can be used to enhance collaborative effort, regulate competing parties, and simulating user preferences. 
		* *Public Health and Intelligent Medical Diagnosis* - aims to improve various fields in healthcare including 
			* Disease prediction, diagnosis, and treatment. MARL is good in this context because it can handle collaborative tasks. 
			* Medical image processing via an ensemble of MARL agents.
		* *Smart Manufacturing* - using AI to optimize the production process. These methods typically require sophisticated [[MARL Deep Learning#Value Decomposition and Common-Reward Games|techniques]] to counteract combinatorial action space explosion.
			* Job shop scheduling - involves resource allocation, task management and scheduling, especially in a dynamic environment. 
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
			* Update the first [[Off Policy Prediction and Control with Approximation#DQN|DQN]] for job routing.
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

* [^Zheng_Trott_2020] AI economist 

[^Zheng_Trott_2020]: Zheng et al. (2020) [The AI Economist: Improving Equality and Productivity with AI-Driven Tax Policies](https://arxiv.org/pdf/2004.13332.pdf) . Supplemental [blog](https://blog.salesforceairesearch.com/the-ai-economist/)
# Links 
* [[Reinforcement Learning]]
* [[Multi-Agent Reinforcement Learning]]