* Unlike other manufacturing frameworks, swarm manufacturing aims to decentralize and generalize to the production of multiple products by having the factory consist of a swarm of mobile manufacturing [[Robotics|robots]] that can recalibrate themselves in real time.

# C3DP
* Cooperative [[Additive Manufacturing|3D printing]] is a task involving printing an object using a swarm of machines with 3D printers. The goal is to reduce print time and i ncrease print scale without needing to increase printer size or reduce print resolution.

* [^poudel_2022] proposes a hardware and software architecture for the cooperative 3D printing (C3DP) task (see image below) validated by both simulation and physical implementation.
	* The proposed software consist of the following modules. The architecture integrates various needs for the C3DP task.
		* **Chunking** - splits the CAD model of the print object into smaller chunks to facilitate multi-robot printing. There are numerous chunking algorithms provided in the system (i.e., chunking from the center outwards or from one side to another) 
		* **Scheduling** - assign chunks to individual robots and schedule printing tasks based on dependency relations between chunks. Assignment is done based on [[Metaheuristics]] so they are not necessarily optimal. The overall print [[Scheduling Problem|schedule]] is then generated based on chunk dependencies. 
		* **Slicing** - generate toolpaths for all the printing robots based on the chunks assigned. To facilitate cooperation between robots, they must be aligned spatially (using the hardware platform) and temporally (using signals between robots.)
		* **Simulating** - animates the printing process to visualize how the printing unfolds. 
	* The hardware platform consists of four main components.
		* A SCARA 3D Printer
		* A mobile platform to transport the SCARA printer from one location to another.
		* A modularized floor tile system for assisting mobile platforms to navigate. They also provide power.
		* A wireless network for communication between SCARA printers and mobile platforms.

![[C3DP Architecture.png]]
<figcaption> C3DP System Architecture. Image taken from Poudel (2022) </figcaption>

[^Poudel_2022]: Poudel et al. (2022) [Toward Swarm Manufacturing: Architecting a Cooperative 3D Printing System](https://asmedigitalcollection.asme.org/manufacturingscience/article/144/8/081004/1133486/Toward-Swarm-Manufacturing-Architecting-a)

# Control
* [^Avhad_2023] conceptualizes an architecture for managing the individual agents inside a swarm manufacturing system, including algorithms for task planning, allocation, scheduling, and communication. 
	* Swarm manufacturing systems are flexible and decentralized. However, to efficiently meet demand, there needs to be a mechanism for directing the swarm. . Complexity in automated task planning is proportional to the complexity of the production environment.
	* The system has the following macro-level [[Factory Optimization Techniques|objectives]]
		* **Strategic**: 
			* High variety
			* Varying volume production
			* Efficient mean makespan for production time.
			* Hybrid control.
			* Cycle Time independent production
		* **Tactical**
			* Topology (factory layout) optimization and deployment
			* Estimation of fleet size 
			* Task Planning
			* Defining safety zones and service points
		* **Tactical-Realtime**
			* Task allocation and scheduling
			* Grid-based material routing
			* Localization and motion planning per robot
			* Local level robot management
	* A swarm manager system has the following objectives. These are in line with managing a multi-agent system.
		* Estimate a plan for an order dispatched from the enterprise layer. The plan is based on the task dependency graph and the current factory topology. 
		* Assigning tasks to robots that can perform the allotted task with minimal temporal cost. Allocation is done using [[Auction Theory|bidding]].
		* Assigning schedules and temporally coordinating the execution of tasks.

![[Swarm Production System.png]]
<figcaption> High Level Swarm Manufacturing System. Image taken from Avhad, Schou and Madsen (2023)  </figcaption>


[^Avhad_2023]: Avhad, Schou, and Madsen (2023) [A framework for multi-robot control in execution of a Swarm Production System](https://www.sciencedirect.com/science/article/pii/S0166361523001318?ref=pdf_download&fr=RR-2&rr=8bd27f94cb2e20fb)

# Links
* [[Network Science]] and [[Complex Systems]] - swarms can be seen as complex systems.
* [[Metaheuristics]] - some metaheuristics also use with swarms to solve problems. 
* [[Swarm Intelligence]]