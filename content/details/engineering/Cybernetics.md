* **Cybernetics** concerns the regulation and [[Control Theory|control]] of [[System Science|systems]].
* This addresses two key issues that systems face:
	* Regulating the constituent subsystems of the system.
	* Responding to the environment including external sources and sinks of energy, matter and information.
# Communications
* *Part of control is [[Information in Systems|communication]] between systems.*
	* The point of communications is to provide processes/systems with information that they can use to respond and do something differently in order to maintain themselves and their functional competence.

* Communications necessitate establishing proper channels between the two communicating subsystems, as well as appropriate protocols to interpret messages between sender and receiver.

* Communications subsystems allow inter-process coordination or cooperation. 
	* *Communication conducive for coordination is typically two-way*. 
	* One-way communication can only work in reactive systems.

# Controlling Complex Systems
* **Asby's Law of Requisite Variety / First Law of Cybernetics** - a [[Complex Systems|complex]], multi-faceted problem can be controlled only by means that have as much complexity (variety) as the problem being addressed

* For more complex systems, pairwise two-way communication is insufficient to coordinate the entire system. Instead, we typically see a form of **hierarchical control** mechanism that coordinates the entire system.
	* Hierarchical control is based on the fact that *there are different layers of control in systems based on the different control decisions* required to keep all underlying processes operating in a coordinated fashion

![[Hierarchical Control.png]]
<figcaption> Hierarchical Control. Image Taken from Mobus and Kalton</figcaption>

* At the lowest level, we see control done through [[Feedback Loop|feedback loops]]. *It is a general principle of cybernetics that self-regulation is done through information feedback*

* All control mechanisms are influenced by various factors.
	* The sampling rate. In some sense *sampling rate dictates how much control we are exerting to the process*.
	* Whether control is done based on continuous or discrete time.
	* The presence of delays and lags in observation, computation, synchronization, reaction, actuation, and effects of control.
		* Computational Delay leads to bounded rationality as there may not be enough time to make an appropriate response
		* Reaction Delay can either cause oscillations or ineffectual control. 
			* *Delays can cause oscillations and drive the system towards an unstable state* because of delayed response from the control mechanism.
	* The presence of noise in incoming signals which may increase processing time in an attempt to filter out noise.
	* Synchronization considerations.
	* The Stability of the control mechanism.

* *Control does not come for free*. There are associated costs to having a control system which must be considered.
	* A controller can lose control due to instabilities that lead to large deviations in expected behavior, which means there is a **cost from damage** incurred by repairing the system. 
	* There is a **cost of responding** since energy must be expended to use the actuators. 
	* There is **cost of maintenance** since the control system itself will degrade over time. 
	* For adaptive response, there is also the **cost of constructing** more or better response mechanisms and maintaining said mechanisms as well as the response construction mechanism. 

* Some forms of control
	* [[PID Control]]
	* [[Adaptive and Anticipatory Control]]

* In practice, within the system as a whole, *control is distributed within the whole system* which necessitates a coordination mechanism for each subprocess and subsystem.
	* Distributed control is more efficient but also necessitates more need for synchronization and coordination
	* There are generally three kinds of coordination mechanisms 
		* **Logistical Control** involves maintaining the overall internal functioning of the subsystems and the distribution of resources to ensure it. This includes the mechanisms for
			* Internal coordination in operations
			* Internal coordination in repair and maintenance.
		* **Tactical Control** involves interacting with the environment -- between internal and external subsystems.

## Logistical Control
* *Distributed control mechanisms in practice tend to couple together*. A hierarchy soon emerges to manage all the coupled control mechanisms.
* Cooperation can transition to coordination when one sub-process takes on the role of coordinator in systems having more than just two sub-processes.
	* Cooperation can evolve into coordination, which produces the beginnings of the control hierarchy.
	* It is at the level of coordinating processes which optimization takes place.
	* A **budget** is a common system archetype found within coordinator processes. This is used to allocate resources to each subprocess with the aim of optimal operations subject to restrictions imposed by the state of the environment or the system.
	* The coordinator needs a [[Systems and Models|model]] of the entire set of sub-processes it controls.
		* In all model building, it is first necessary to understand the micro-flows between processes
		* As a general rule, *coordination models operate on a larger time scale than the processes they coordinate*
	* Coordinators may also make use of **buffers** which hold excess resources or energy while other work processes catch up. The buffer acts as a temporary source for these slower processes.
		* A general rule: The timing of outputs from one process does not always coincide with the input timing needed by the process that receives the outputs.
* *Processes that maintain processes need to be coordinated just as primary processors do*

* Complexity follows as we try to *coordinate coordination itself*.  [^prog]
	* Problems arise when coordinators do not distinguish between when they are being coordinators or coordinator of coordinators and a direct feedback controller of operations.
	* Complexity drives the need for complex layers of coordination and administration.
[^prog]: An analogy can be drawn to [[Programming]] with how routines manage subroutines which manage other subroutines. 


## Tactical Control
* The system must monitor the sources and sinks of its environment in such a way as to be able to adjust its own overall behavior.
* The system must be able to adjust its own behavior so as to optimize its access and receipt of resources as well as to fulfill its needs and dispose of its waste products. 

* **Interface Processes** are flows between a system and its environment.
	* The interface is comprised of boundary conditions which constraint flows into the system based on what the system expects.
	* A **passive interface** is any subprocess that receives inputs from an external source where that source provides the energy (pressure) to move the substance. 
	* An **active interface** is any subprocess that receives inputs from an external source where the system itself provides the energy to move the substance.

* Coordination with the environment is achieved by *changing the system relative to the environment*.
* Coordination with the environment requires a constant flow of data. Typically this comes in the form of feed-forward information. 

* A more sophisticated tactical coordination approach is to *use models of the sources and sinks* that provide longer-term anticipation of deviations in supplies and output acceptances and communications with key sources and sinks.
	* *Tactical models tend to be simple since they only operate on short time scales*.

## Strategic Models
* Systems with a **strategic model** have developed the capacity to plan out alternative behaviors directed towards a given objective.
* Unlike tactics, strategy is more complex and long term.

* **The Basic Strategic Problem**: Complex Systems that exist and function in a complex environment must be able to do more than just react to short-term fluctuations in the environment. 
	* This problem extends to the problem of dealing not just with known environmental factors but also [[Statistics|unknowns]]. 

* Strategic models necessitate more than just environmental models and historic records. It requires a model of the self and the environment and how they interact. 
	* From the environment, the self-model identifies threats and opportunities
	* From the self, the self-model identifies strengths and weaknesses.
* *The essence of strategy is being able to control behavior based on a projection of a near future possible scenario*. 

* Another aspect of strategic management is [[The Exploitation-Exploration Trade-Off]]. 

* The output of the strategic model's analysis and decisions is a long-term plan that sets goals to be achieved by the whole system and then translates those goals into a series of sub-goals that can be handed off to the coordination level controllers
	* The strategic model must also account for plans necessitating change due to the stochastic nature of the environment .

## Control Hierarchy
* *Control typically is distributed among levels of a hierarchy based on functional requirements*.
* Hierarchy emerges from the inherent dynamics of coordination, for coordinated units become merged in a higher-level unity
![[Control Hierarchy.png]]
<figcaption> Control Hierarchy. Image taken from Mobus and Kalton </figcaption>


* By their systemness, one complication to keep in mind is when *the role of coordinating processes conflicts with its own functions as a system.*. 

* Hierarchical Management can fall apart because . . . 
	* **Environmental Overload**:  The environment of the system changes too much, too quickly, or in unpredictable ways that overcome the resilience afforded by the control system.
		* **Information Overload** - the inability to process [[Information in Systems|information]] that comes too quickly or too often that exceeds the system's computational load and ability to convert information to knowledge.
		* **Force Overload**  - physical stressors that act on the system exert a force that exceeds the system's homeostatic mechanisms.
		* **Resource Depletion** - systems consume nonrenewable resources or renewable resources faster than it can be renewed. 
			* **Liebig's Law of the Minimum**: Growing systems cannot grow beyond a limit imposed by the limiting resources. 
	* **Internal Breakdown**:  Critical internal mechanisms in the control hierarchy break down due to entropy or targeted disruptions (see [[Network Robustness]] for more).
		* **Entropic Decay**- subsystems wear out due to wear and tear. If they cannot be repaired at critical moments, then the control structure breaks down.
		* **Point Mutation** - targeting aspects of the control mechanism which alter how they function or render them inoperable. 
	* **Imperfect Components**: Especially for human-based systems, the inability to act [[Game Theory|perfectly rational]] or predictably. 
		* **Stochasticity** - subsystems do not behave within expected performance metrics which causes the system to fail as it is not equipped.
		* **[[False Priors|Heuristics]]** - the use of rules of thumb that are fast but inaccurate
		* **Internally Motivated Agents** - humans are [[Human Biases|biased]] and not perfectly rational which causes breakdowns in a human-based system, especially when people act based on their self interest in a way that is not Pareto-optimal.

* In an evolutionary sense, control structures [[System Evolution|evolve]] from the bottom up by virtue of increasing complexity as more complexity = control structures break down which necessitates higher order control. 
# Links
* [[Principles of Systems Science by Mobus and Kalton]]
* [[System Dynamics]]