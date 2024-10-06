* **Complex Systems** generally have the following properties:
	* They have **emergent** behaviors -- the dynamics are not easily predictable even when the initial conditions remain seemingly the same
	* They require a considerable amount of work be done to [[Systems and Models|understand]] them
	* Complex systems cannot be easily described.

# Defining Complexity 
## Complexity as Hierarchy
* One perspective for defining complexity uses [[Networks in Systems|hierarchies]]. There are three kinds
	* **Relational Complexity** - there are many edges in the interaction network of the system.
	* **Compositional Complexity** - the system has many kinds of vertices.
	* **Structural Complexity** - the system is both relationally and compositionally complex. Additionally, there are many kinds of edges representing many possible interactions between components.

* *Having multiple constituent parts is not a prerequisite for complexity.

* The number of levels of organization from the atomic elements of the system to the system itself is a measure of the complexity of the system
* An important factor as we move up the levels of organization is that *the interactions between constituents are constrained in some way so as to limit the possible configurations of constituents*.
* Functionally entities that have transitory relations with one another can develop significant complexity in terms of patterns of those relations. *[[System Dynamics|Dynamic]] systems can develop cycles of interactions that recur regularly in time.*


* Complex systems are also said to have a **functional hierarchy**  wherein components are connected by flows between components, subsystems and the environment.
	* This is hierarchical because components of a system tend to be coupled the most to each other than to any external system.
	* Also, the system's functions are carried out thanks to the functions of each of its components. 

* *Structural Hierarchy is tied to Functional Hierarchy*.  In fact *Hierarchy is a response to an increase in complexity*.

## Complexity of Processes
* The complexity of a system, particularly a system that can perform computation or solve problems, can be defined in terms of **[[Asymptotic Analysis|Time Complexity]] and Space Complexity**.
	* See more on this [[Complexity Theory|here]].
	* This extends not just to computers, however. In fact, we can use time complexity as a measure  for the amount of work necessary to complete a task. 
	* In this perspective, systems can still exhibit hierarchies. For example, in the case of [[Multiprogramming|Parallel computation]] or having [[Swarm Intelligence|multiple components perform computation]] in a distributed manner.

* Another perspective deals with **Information Complexity** which pertains to the amount of [[Information Theory|information]] admitted by the system.
	* Systems need to be able to encode a minimum amount of information to produce output.
	* More complex systems encode more bits of information.

## Behavioral Complexity
* Complexity can come from simple rules of interaction.
* One example comes from [[Cellular Automata|Cellular Automata]]
* Another comes from [[Fractal|fractals]] and [[Chaos Theory|chaotic]] dynamics. Here, the complexity comes from nested structures and unpredictable behaviors.

## Organization
* *Complexity can be tied to the entropy of a system*. 
* Consider that objects in a system need not be coupled. However, coupling introduces a functional hierarchy.
* **Organized Complexity** pertains to complexity observed in systems where there are many parts coupled to each other  and where the dynamics of the system itself minimizes the internal entropy (disorderliness) of the system. 

## Potential and Realized Complexity

* **Potential Complexity** - a measure of complexity which takes into account: 
	* The boundary formed that objectifies the system.
	* The number of kinds of components within the boundary or that can pass through the boundary.
	* The number of components present for each kind.
	* The number of kinds of possible interactions between all combinations of component types
	* The number of kinds of energies (matter) and their potential differences between sources and sinks.
	* The geometry of the system with respect to its boundaries.
	* The location of energies (sources and sinks) along the boundary.
* *Potential Complexity pertains to all possible ways that components can be combined together*

* **Realized Complexity** - a measure of complexity regarding how the parts are organized, connected, and function together. 
	* It is a challenge for systems science to figure out, with hindsight, the process of transforming, evolving connectivity that has brought about a realized complexity of a system
	* *Realized Complexity pertains to what would be observed due to constraints such as scarcity or geometric configuration*.  It looks at the system as it actually would be at a given point in time.

* *Realized Complexity tends to be much smaller than Potential Complexity.*
* Potential Complexity within a layer of organization can increase or decrease with respect to the previous layer.
	* If it increases, it means that there are many ways to combine components from the previous layer. In particular, there are many interaction potentials between components with few constraints. 
	* If it decreases, it means that either:
		* There are only a few ways for the components to combine to be functional subsystems, usually indicative of additional constraints.
		* There exists [[System Control|control systems]] that manage the complexity. 

# Pathologies of Complexity
* **Resilience** pertains to the system's ability to recover and restore its function subsequent to some disruptive event,

* *Complex systems are not necessarily resilient*
* Some events may be **black swans** -- unexpected or low probability events which the system is not built to handle.
* A system may have **brittle connectivity** -- connection between components cannot be altered without having drastic effects on other parts of the system.
	* Sometimes brittle connectivity is in itself a response to added complexity. 


* **Component Failure** can also happen, where one or more components within the network suffer some form of degradation in personality
	* *This all boils down to the [[Thermodynamics|second law of thermodynamics]]*. Entropy will always make the system tend to disorder.
	* Brittle systems can also come from [[Network Robustness|brittle networks]].

* **Process failures** come in the form of disruptions in the process flow -- that is, failures in some other system in the chain of inputs or outputs to the system of interest. 
	* Note that sometimes, if such disruptions are common, the system will have a tendency to incorporate more complexity to adapt.
	* Nonlinear dynamics and positive feedback loops in critical subsystems make the system unstable, and thus the process flow unstable. 

* The more things in a system, the more complex it is and the more things can go wrong.
	* Such disruptions may even **cascade** throughout the system if the underlying network is brittle. 
	* Disruptions may *propagate* outward to other systems and even be amplified with positive feedback loops
	* In this sense, *systems can grow too big for their own good* (see [[System Archetypes|here]]).  Law of Diminishing returns tends to apply for any benefit that added complexity brings up to the point that *Complexity itself becomes the problem*.
# Control
* Systems that are overly complex at a given level of organization tend to have numerous stability problems due to an adequate method of coordinating the behaviors (functions) of numerous interacting components.

# Links
* [[Principles of Systems Science by Mobus and Kalton]]

* [[Characterizing Systems]]
* [[Universal Properties of Systems]]