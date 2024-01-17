* [^1] A **system** is an interconnected set of elements that is coherently organized in a structure, and which produces a characteristic set of behaviors. 
* A system is more than the sum of its parts. The *elements* of a system are usually the easiest parts to notice.
* We can define the system more formally. A system $S_l=(C,N,I,B,K,H)_l$ where 
	* $l$ is the *index* related to the level of complexity,.
		* The system of interest having $l=0$ is at the top. 
		* When $C$ is decomposed and each $c_i$ is treated as its own system, $S_{1,i}$, we have a new system with level of complexity $l'=l+1$
	* $C$ is a multiset of of *component subsystems* $\{(c_1,n_1), \dots (c_k,n_k)\}$ where 
		* $c_i$ is the *type* and may be a subsystem at lower complexity level.  
		* $n_i$ is an integer enumeration of the number of components of the particular type.
		* The number of times a tuple appears is equal to the number of variations of that tuple 
	* $N$ is a *[[Fundamental Constructs of Network Science|network]] description* of the system, in particular which components are connected and at what level of complexity. 
	* $I$ is a graph where half of the nodes are entities in the environment, the other half are component subsystems .Edges indicate the *connections between objects in the environment and objects in the subsystem*
	* $B$ is a complex object that describes the *boundaries* of the system. 
	* $K$ is a complex object that describes the *dynamics* -- that is, how the components interact with each other and the environment. 
	* $H$ is a a complex object of the *history* of the system or its state transitions as it develops. 
[^1]: Properties are from [[Principles of Systems Science by Mobus and Kalton|Mobus and Kalton]] - Ch. 1.4
# Principles of Systems 
## Systemness
* Systems are bounded objects that can be delineated from the environment with *boundaries*. Such boundaries are either real or arbitrarily set.
* Systems can be *nested* -- containing smaller subsystems.  *The whole contains parts and yet the whole is also more than the sum of its parts*


* Changing a system's elements, interconnections or purposes *changes* its behavior.

* As new levels of complex organization emerge, the new levels intertwine in dynamic systemic relationships with other levels. In particular we can consider four levels 
	* **Ontological** - systems in the world / observable universe. It is primarily concerned with parts and wholes. This is what the Natural Sciences study.
	* **[[Epistemology|Epistemological]]** - systems in the mind or relating to knowledge and information as perceived by an observer. These are formed in the brain. This is studied by the Social Sciences
	* **Abstract** - [[Mathematics]] or symbolic [[Linguistics|language]] aspect. 
	* **Software** -  systems in software.

## Processes 
* *Systems are Processes Organized in Structural and Functional Units
* The least obvious part of the system, its *function or purpose*, is often the most crucial determinant of the system’s behavior, and it can only be deduced by examining this behavior. 
* System *structure* is the source of system behavior. System behavior reveals itself as a series of events over time. The structure comes from interrelated stocks, flows, and feedback loops.

## Networks 
* *Systems are [[Graph Theory|networks]] of relations among components and can be represented abstractly as such network of relations*. 
* Many of the *interconnections* in systems operate through the flow of information (via decisions or actions) or resources. These serve to hold the system together and determines how it operates. 

## Dynamic 
* *Systems are dynamic over multiple spatial and time scales*. 
* Systems constantly adjust themselves by feedback loops , but when interdependent components operate with feedback loops of different temporal scales, the system may become unstable

## Complexity 
* *Systems exhibit various kinds and levels of complexity*. 
* [[Complex Systems|Complexity]] and nonlinearity can, themselves, be sources of disruption or failure.
* The purpose of a system may be *emergent* and even accidental -- as in no actor intends for such to happen but the structure of the system makes it so. 

## Evolving 
* *Systems evolve*. Either towards higher organizations, maintaining a steady-state, or decaying.
* The evolution of systems is based on its flows. When inflows are too low, entropy takes over and the system deteriorates towards disorder 

## Information 
* *Systems encode knowledge and receive and send information*. 
* The system, by its very own structure, knows how to react to a situation.

## Regulation 
* *Systems have regulatory subsystems to achieve stability*. 
* As systems evolve toward greater complexity, the interactions between different levels of subsystems require coordination and control in the form of feedback loops

## Models of Others 
* *Systems can contain models of other systems*. 
* Systems and subsystems can expect certain forms of systemic relations to be present. In general, systems encode in some form models of the environment or aspects of the environment with which they interact

## Models of Themselves 
* *Sufficiently Complex, Adaptive Systems Can Contain Models of Themselves*
* Adaptive systems can modify their models of an environment and of themselves to better adapt to the dynamics of the environment 

## Understandability 
* *Systems can be understood* 
* In principle systems function in terms of relational dynamics , and this is an appropriate object for human understanding Systems afford predictability by constructing and testing models 

## Improvability 
* *Systems can be improved*. 
* Systems account of evolution will have to take up the question of when and how causal functioning gets to the condition where the operation of the system can be observed to aim selectively at some kind of result.
# Universal Properties 
## Wholeness 
* There are *identifiable objects* or things that are composed of parts that interrelate to one another in some kind of organized fashion
* *There exists a boundary which differentiates an object from its environment*.
	* A **Concrete Boundary** is one where *the demarcation between the internals of the object and the surrounding environment is localized in time and space*-- that is, it is clear via spatial coordinates if we are inside the object, and "being inside" is treated as an event in time.
		* More generally, boundaries can be formed at the periphery of a unitary system when there are components that have a natural ability to *interact preferentially* with each other and/or with more inward positioned components
		* If the coupling with internal or other boundary objects is stronger than that of external objects, a physical boundary naturally forms and maintains itself.
	* A **Porous Boundary** is one that *allows the import and export of materials or information*
	* A **Fuzzy Boundary** is one where *there is no discrete transition from inside to outside* It is not apparent when we are inside or outside the system. 
		* It arises when the substance is not sufficiently differentiable from the surroundings of the system.
	* A **Conceptual Boundary** is one *arbitrarily selected for the matter of convenience or analysis*.
		* It is not truly arbitrary since it is (typically) based on something about the system. 

## Composition 
* *Systems are composed of subsystems and their interactions with one another*. 
* Each component of a system has its own **personality** -- that is, they expose various interaction potentials at their boundaries.  *Each component can interact with other components in various ways*. 

* A **module** is a component subsystem that has a concrete boundary and a stable set of interaction potentials. 
* A **systemic overlap** is a compositional strategy with fuzzier boundaries and less defined or less stable interaction potentials.
	* Typically, systems with overlap have redundancy for resiliency.

* Overlap can also come from overlapping the functions of a single component to serve multiple purposes at different times [^overlap_1]

[^overlap_1]: Analogous to [[Object Oriented Programming]] where we have modules that may sometimes have overlap with each other.  

* *Usually at the boundary, subsystem components appear as black boxes to one another*. The more complex the subsystem components are, the more degrees of freedom they have in terms of what they take as input or produce as output at any given instant

* *Systems can be homogeneous or heterogeneous* with respect to how many different kinds of components constitute the system. 
	* More homogeneous compositions correspond to a simpler internal structure and function 
	* More heterogeneous compositions correspond to more complex structures and more possible interactions 

## Internal Organization and Structure 
* **Structure** refers to the way components are stably linked to one another to form **patterns** that persist over time. 
* **Organization** concerns both internal structure and how internal structure leads to function.

* **[[Graph Connectivity|Connectivity]]** means that components in a system can form connections based on their interaction potentials 
	* The **coupling strength** is the amount of change that will be effected in one component as a result of changes in another component 
		* Direct connection typically implies high coupling. 
		* Couplings can be transitive where $A$ affects $B$ and $B$ affects $C$. Thus *high transitivity means changes cascade across the system*.
		* The strength between two components decreases with the number of intermediate connections and increases with some factor of attenuation.
		* Couplings can be *weak* which means they can be broken depending on the dynamics of the system. Alternatively, they can be *strong* and persist. 
		* *Strong couplings imply more stable and persistent systems*. 
	* Connections can be formed through attractive or repulsive **forces** [^conn_1]. 
		* Attractive forces result in components being brought closer together and forming clusters 
		* Repulsive forces result in components being brought further apart and dispersing. 
		* *The causality of these forces relates to the level of the system observed but attraction an repulsion themselves appear to be universal* [^conn_2]
	* **Flows** are special forces in which something moves from one place to another 
		* Components that are strongly coupled due to flows transfer more material through the flow channel. 
		* *In a closed system all outflows of one subsystem become inflows of another.*
		* It is common to see material, energy and information as flowing into a component. The component then performs work and outputs a usable product, waste materials, and waste heat (i.e., unusable energy).

* *In general, the forces and flows connecting components are stronger than at the next higher scale of complexity*.
	* Because of this ,components can exist in a hierarchy. 
	* In the hierarchy, overlapping subsystems are represented as shared components.

* **Complexity** - hierarchy gives rise to complexity. 
	* **Potential Complexity** - a measure of complexity which takes into account 
		* the number of kinds of components
		* the number of kinds of possible interactions between all combinations of component types
		* the number of objects of each type of component contained within the boundary of the system. 
	* **Realized Complexity** - a measure of complexity regarding how the parts are organized, connected, and function together. 
		* It is a challenge for systems science to figure out, with hindsight, the process of transforming, evolving connectivity that has brought this realization

* **Networks** - all systems may be described as organizations based on networks of components and their various interconnections/interactions through forces and flows

* *Systems transform inputs into outputs*
	* A **function** or **purpose** is a process that transforms inputs into outputs. Purpose is used for systems aimed at something, otherwise we use function 
	* *Functions exist in a hierarchy* where nodes correspond to functions and edges correspond to connections based on inputs and outputs. 
	* *Functions and Purposes can be emergent* 

[^conn_1]: Taking inspiration from [[Physics]].
[^conn_2]: Universal in the sense that many systems feature these forces although why these forces exist vary from system to system. 

## External Organization 
* The **environment** consists of things that are considered not part of the system in study. 
* *In the case of the real world, no system exists in a vacuum [^ext_org_1]*. Thus, the environment can be characterized with sources and sinks

* **Dissipative Systems** - systems that maintain themselves by continually taking in and dispelling matter, energy, and information. 

* *It is important to examine the flows coming from the environment*
	* The internal organization of a system can be maintained using constraints that allow only certain flows from the environment.
	* Information flows are always mediated, carried by some kind of flow of matter or energy
	* *Diffusion is a universal principle for physical systems* [^ext_org_2]. Substances in a concentration will always attempt to disperse within the boundaries. 
	* *Because of diffusion, we can also study gradients to see how differences make a difference*. 

[^ext_org_1]: From the First Law of Thermodynamics
[^ext_org_2]: From the Second Law of Thermodynamics 

# Links 
* [[System Dynamics]]
* [[Thinking in Systems by Meadows]] - Ch. 1
* [[Principles of Systems Science by Mobus and Kalton]] - Ch. 1 - 3