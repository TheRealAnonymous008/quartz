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

* *Distributed control mechanisms in practice tend to couple together*. A hierarchy soon emerges to manage all the coupled control mechanisms.
* Cooperation can transition to coordination when one sub-process takes on the role of coordinator in systems having more than just two sub-processes.
	* Cooperation can evolve into coordination, which produces the beginnings of the control hierarchy.
	* It is at the level of coordinating processes which optimization takes place.
	* A **budget** is a common system archetype found within coordinator processes. This is used to allocate resources to each subprocess with the aim of optimal operations subject to restrictions imposed by the state of the environment or the system.
	* The coordinator needs a [[Systems and Models|model]] of the entire set of sub-processes it controls.
	* Coordinators may also make use of **buffers** which hold excess resources or energy while other work processes catch up. The buffer acts as a temporary source for these slower processes.
# Links
* [[Principles of Systems Science by Mobus and Kalton]]
* [[System Dynamics]]