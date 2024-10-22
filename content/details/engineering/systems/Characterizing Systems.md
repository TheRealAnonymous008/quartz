* [^1] A **system** is an interconnected set of elements that is coherently organized in a structure, and which produces a characteristic set of behaviors. 
* We can define the system more formally. A **system** $S_l=(C,N,I,B,K,H)_l$ where 
	* $l$ is the **index** related to the level of complexity,.
		* The system of interest having $l=0$ is at the top. 
		* When $C$ is decomposed and each $c_i$ is treated as its own system, $S_{1,i}$, we have a new system with level of complexity $l'=l+1$
	* $C$ is a multiset of of **component subsystems** $\{(c_1,n_1), \dots (c_k,n_k)\}$ where 
		* $c_i$ is the **type** and may be a subsystem at lower complexity (at level $l+1$).
		* $n_i$ is an integer enumeration of the number of components of the particular type.
		* The number of times a tuple appears is equal to the number of variations of that tuple 
	* $N$ is a **[[Fundamental Constructs of Network Science|network]] description** of the system, in particular which internal components are connected and at what level of complexity. 
	* $I$ is a [[Graph Theory|bipartite graph]] where half of the nodes are entities in the environment, the other half are component subsystems .Edges indicate the **connections** *between objects in the environment and objects in the subsystem*
	* $B$ is a complex object that describes the **boundaries** of the system. 
	* $K$ is a complex object that describes the **dynamics** -- that is, how the components interact with each other and the environment. 
	* $H$ is a complex object of the **history** of the system or its state transitions as it develops. 

[^1]: Properties are from [[Principles of Systems Science by Mobus and Kalton|Mobus and Kalton]] - Ch. 1.4
# Principles of Systems 
## Systemness
* Systems are bounded objects that can be delineated from the environment with *boundaries*. Such boundaries are either real or arbitrarily set.
* Systems can be *nested* -- containing smaller subsystems.  *The whole contains parts and yet the whole is also more than the sum of its parts*
* Changing a system's elements, interconnections or purposes *changes* its behavior.

* As new levels of complex organization emerge, the new levels intertwine in dynamic systemic relationships with other levels. In particular we can consider four levels 
	* **Ontological** - systems in the world / observable universe. It is primarily concerned with parts and wholes. This is what the [[Science|Natural Sciences]] study.
	* **[[Epistemology|Epistemological]]** - systems in the mind or relating to knowledge and information as perceived by an observer. These are formed in the brain. This is studied by the [[Social Biases|Social Sciences]].
	* **Abstract** - [[Mathematics]] or symbolic [[Linguistics|language]] aspect. The abstract is either made concrete either through concrete measurements (i.e., in the Sciences) or through Natural [[Linguistics|language]]. 
	* **Software** -  Systems in [[Software Engineering|Software]]

![[System Domains.png]]
<figcaption> Domains in Systems. Image taken from Mobus and Kalton </figcaption>

* See more [[Universal Properties of Systems|here]]
## Processes 
* *Systems are Processes Organized in Structural and Functional Units
* The least obvious part of the system, its *function or purpose*, is often the most crucial determinant of the system’s behavior, and it can only be deduced by examining this behavior. 
* *System structure is the source of system behavior*. System behavior reveals itself as a series of events over time. The structure comes from interrelated stocks, flows, and [[Feedback Loop|feedback loops]].
* See more [[Universal Properties of Systems|here]]
## Networks 
* *Systems are [[Graph Theory|networks]] of relations among components and can be represented abstractly as such network of relations*. 
* Many of the *interconnections* in systems operate through the flow of information (via decisions or actions) or resources. These serve to hold the system together and determines how it operates. 
* See more [[Networks in Systems|here]].
## Dynamics 
* *Systems are dynamic over multiple spatial and time scales*. 
* Systems constantly adjust themselves by feedback loops , but when interdependent components operate with feedback loops of different temporal scales, the system may become unstable
* In general for the dynamics of the system, the lower the resolution in spatial dimensions, the lower the resolution in the temporal dimensions.
* See more [[System Dynamics|here]].
## Complexity 
* *Systems exhibit various kinds and levels of complexity*. 
* The purpose of a system may be *emergent* and even accidental -- as in no actor intends for such to happen but the structure of the system makes it so. 
* [[Complex Systems|Complexity]] and nonlinearity can, themselves, be sources of disruption or failure.
* See more [[Complex Systems|here]].
## Evolution
* *Systems evolve*. Either towards higher organizations, maintaining a steady-state, or decaying.
* The evolution of systems is based on its flows. When inflows are too low, entropy takes over and the system deteriorates towards disorder 

## Information 
* *Systems encode knowledge and receive and send [[Information Theory|information]]*. 
* The system, by its very own structure, knows how to react to a situation.
* [[Information in Systems]]
* [[Theory of Computation]] - part of processing information is some form of computation.

## Regulation 
* *Systems have regulatory subsystems to achieve stability*. 
* As systems evolve toward greater complexity, the interactions between different levels of subsystems require coordination and [[Cybernetics|control]] in the form of feedback loops

## Models of Others 
* *Systems can contain models of other systems*. 
* Systems and subsystems can expect certain forms of systemic relations to be present. In general, systems encode in some form models of the environment or aspects of the environment with which they interact
* See more [[Systems and Models|here]].

## Models of Themselves 
* *Sufficiently Complex, Adaptive Systems Can Contain Models of Themselves*
* Adaptive systems can modify their models of an environment and of themselves to better adapt to the dynamics of the environment 
* See more [[Systems and Models|here]].

## Understandability 
* *Systems can be understood* 
* In principle systems function in terms of relational dynamics , and this is an appropriate object for human understanding.
* Systems afford predictability by constructing and testing models.
* Even though systems are black boxes, we can study their functions and develop models about the internals of the system.
* Modeling is made more complicated by the fact that observers are typically part of the system they are observing. Thus, the observers themselves can change the system and the observations they make are not necessarily objective truths about the system (see [[Confirmation Bias|observer bias]]).
* See more [[Systems and Models|here]].

## Improvability 
* *Systems can be improved*. 
* A systems-oriented account of evolution will have to take up the question of when and how causal functioning gets to the condition where the operation of the system can be observed to aim selectively at some kind of result. That is, *there is a metric of interest that is improved over time as a result of evolutionary processes.*


# Links 
* [[System Dynamics]]
* [[Thinking in Systems by Meadows]] - Ch. 1
* [[Principles of Systems Science by Mobus and Kalton]] - Ch. 1 - 3