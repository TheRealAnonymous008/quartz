# Boundaries
* There are *identifiable objects* or things that are composed of parts that interrelate to one another in some kind of organized fashion.
* *There exists a boundary which differentiates an object from its environment*.
	* A **Concrete Boundary** is one where *the demarcation between the internals of the object and the surrounding environment is localized in time and space*-- that is, it is clear via spatial coordinates if we are inside the object, and "being inside" is treated as an event in time.
		* More generally, boundaries can be formed at the periphery of a unitary system when there are components that have a natural ability to *interact preferentially* with each other and/or with more inward positioned components
		* If the coupling with internal or other boundary objects is stronger than that of external objects, a physical boundary naturally forms and maintains itself.
	* A **Porous Boundary** is one that *allows the import and export of materials or information*
	* A **Fuzzy Boundary** is one where *there is no discrete transition from inside to outside* It is not apparent when we are inside or outside the system. 
		* It arises when the substances that make the boundary are not sufficiently differentiable from the surroundings of the system.
	* A **Conceptual Boundary** is one *arbitrarily selected for the matter of convenience or analysis*.
		* It is not truly arbitrary since it is (typically) based on something about the system. 
		* It is important to remember that systems are part of other systems .Therefore, this boundary is useful in so far as analyzing a system of interest.
* We say that anything inside the boundary is "**in**" the system (or is part of the system). Anything else is in the **environment**.
* From the outside looking in, a system acts as a black box.
# Composition 
* *Systems are composed of subsystems and their interactions with one another*. 
* A **component** pertains to whole entities that can be treated as black boxes -- that is, analyzed without decomposing further to subsystems .
* Each component of a (complex) system has its own **personality** -- that is, they expose various interaction potentials at their boundaries.  *Each component can interact with other components in various ways*. 

* A **module** is a component subsystem that has a concrete boundary and a stable set of interaction potentials. 
* A **systemic overlap** is a compositional strategy with component subsystems that have fuzzier boundaries and less defined or less stable interaction potentials.
* We can see two forms of compositional strategy
	* **Systemic Overlap** makes use of systemic overlap. In which case, it has redundant elements to add resilience
	* **Functional Overlap** can also come from overlapping the functions of a single component to serve multiple purposes at different times [^overlap_1]

[^overlap_1]: Analogous to [[Object Oriented Programming]] where we can have routines that are called by multiple classes.

* *Usually at the boundary, subsystem components appear as black boxes to one another*. 
	* The more complex the subsystem components are, the more degrees of freedom they have in terms of what they take as input or produce as output at any given instant
	* The more complex the components are, the harder it is to obtain a high level of regularity in how these systems interact since there are more possible interactions.

* *Systems can be homogeneous or heterogeneous* with respect to how many different kinds of components constitute the system. 
	* More homogeneous compositions correspond to a simpler internal structure and function 
	* More heterogeneous compositions correspond to more complex structures and more possible interactions 

# Internal Organization and Structure 
* **Structure** refers to the way components are stably linked to one another to form **[[Pattern Structure|patterns]]** that persist over time. 
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
		* The strength of the flow channel is measured by the amount of "stuff" transferred per time. 
		* Components that are strongly coupled due to flows transfer more material through the flow channel. 
		* *In a closed system all outflows of one subsystem become inflows of another.* [^ext_org_1]
		* It is common to see material, [[Work and Energy|energy]] and information as flowing into a component. The component then performs work and outputs a usable product, waste materials, and waste heat (i.e., unusable energy).

![[Systemic Flow.png]]
<figcaption> Systemic Flow. Image taken from Mobus and Kalton </figcaption>

* *In general, the forces and flows connecting components are stronger than at the next higher scale of complexity*.
	* In essence, coupling forces define the wholeness of a subsystem, even if it is part of a larger system. 
	* Because of this ,components can exist in a hierarchy. 
	* In the hierarchy, overlapping subsystems are represented as shared components. In fact, *Composition is inherently hierarchical*

* Hierarchy gives rise to [[Complex Systems|complexity]]. 
* **[[Network Science|Networks]]** - all systems may be described as organizations based on networks of components and their various interconnections/interactions through forces and flows

* *Systems transform inputs into outputs*
	* A **function** or **purpose** is a process that transforms inputs into outputs. Purpose is used for systems aimed at something, otherwise we use function 
	* *Functions exist in a hierarchy* where nodes correspond to functions and edges correspond to connections based on inputs and outputs. 
	* *Functions and Purposes can be emergent* 

[^conn_1]: Taking inspiration from [[Physics]].
[^conn_2]: Universal in the sense that many systems feature these forces although why these forces exist vary from system to system and sometimes we do not know the precise "why" behind these forces. 

# External Organization 
* The **environment** consists of things that are considered not part of the system in study. 
* *In the case of the real world, no system exists in a vacuum [^ext_org_1]*. Thus, the environment can be characterized with sources and sinks where material flows into and out of.

* **Dissipative Systems** - systems that maintain themselves by continually taking in and dispelling matter, energy, and information 

* *It is important to examine the flows coming from the environment*
	* The internal organization of a system can be maintained using constraints that allow only certain flows from the environment.
	* Information flows are always mediated, carried by some kind of flow of matter or energy
	* *Diffusion is a universal principle for physical systems* [^ext_org_2]. Substances in a concentration will always attempt to disperse within the boundaries. 
	* *Because of diffusion, we can also study gradients to see how differences make a difference*. That is, gradients tell us information about the environment, and diffusion introduces information channels.

[^ext_org_1]: From the First Law of [[Thermodynamics]]
[^ext_org_2]: From the Second Law of Thermodynamics 

* The boundaries of a system mediate exchange between the inside and the outside. Thus, *boundary conditions help us understand the system's relation to its environment.*
	* Supposing a system can sustain its internal organization, naturally, there must be constraints in what is permitted to flow in and out of the boundary to the system since the system should permit material flow if and only if it contributes to the system's growth.
	  
	  That is *systemic organization involves the emergence of spatiotemporal constraints at the boundary*.
	* Since information is also governed by the flow of matter or energy, the boundary conditions also govern the exchange of information between the environment and the system.

# Links
* [[Thinking in Systems by Meadows]]
* [[Principles of Systems Science by Mobus and Kalton]]