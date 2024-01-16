* [^1] A **system** is an interconnected set of elements that is coherently organized in a structure, and which produces a characteristic set of behaviors. This is its **function** (for human-based systems) or **purpose** (for-non-human based systems)
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
# Principles of Systems 
[^1]: Properties are from [[Principles of Systems Science by Mobus and Kalton|Mobus and Kalton]] - Ch. 1.4
## Systemness
* Systems are bounded objects that can be delineated from the environment with *boundaries*. Such boundaries are either real or arbitrarily set. 
	* Anything outside of the boundaries are outside of the system. *From the outside, the system appears opaque* and we can only infer or speculate on how the system works through how it behaves through the use of models. 
	* Anything inside the boundaries is inside the system. *From the inside, the system appears to be a part of a larger system*. An observer from inside the system must be aware that it is prone to bias, and that it is also a component of the system using its subjective abilities to observe the system in an objective way. 
* Systems can be *nested* -- containing smaller subsystems.  *The whole contains parts and yet the whole is also more than the sum of its parts*


* Changing a system's elements, interconnections or purposes *changes* its behavior.


* As new levels of complex organization emerge, the new levels intertwine in dynamic systemic relationships with other levels. In particular we can consider four levels 
	* **Ontological** - systems in the world / observable universe. It is primarily concerned with parts and wholes. This is what the Natural Sciences study.
	* **[[Epistemology|Epistemological]]** - systems in the mind or relating to knowledge and information as perceived by an observer. These are formed in the brain. This is studied by the Social Sciences
		* *Information is the news of differences*. It talks about facts in the system which are relevant for the specific analysis being conducted. 
		* *Knowledge is the base of patterned expectation*. We use knowledge to assess information.
		* *A crucial feedback loop is how information reinforces knowledge and knowledge gives more ways to interpret information*. The [[Trade Offs#Freedom of Choice Trade-Off|tradeoff between flexibility and rigidity]] exists. 
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
* Complexity and nonlinearity can, themselves, be sources of disruption or failure.
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


# Desirable Properties 
* **Resilience** - the ability of the system to survive and persist within a variable environment. 
	* It arises from a rich structure of many feedback loops that can work in different ways to restore a system even after a large perturbation 
	* The system should have many, different, and potentially redundant balancing loops. 
	* **Meta-resilience** comes from the ability to restore or rebuild feedback loops. 
	* **Meta-meta-resilience** comes from the ability of feedback loops to [[Artificial Intelligence|learn, create and evolve]] complex, restorative, self-organizing structures. 
	* *Resilience does not imply constancy, in fact, rigidity proves to be the opposite of resilience.* 
	* Resilience is not so obvious without a whole-systems view. It is often sacrificed for something short-term. 
	* Resilience expands the possibilities afforded by the system, allowing it to explore more states without destabilizing. 

* **Self-organization** - the capacity of a system to make its own structure more complex. 
	* It produces heterogeneity and unpredictability. It can make new structures, but it requires the [[The Exploitation-Exploration Trade-Off|ability to experiment]]. 
	* These systems diversify and complexify, often from just [[Complex Systems|simple rules]].

* **Hierarchy** - as a consequence of self-organization, a hierarchy emerges. 
	* A complex system can  evolve from a simple system only if there are stable intermediate forms. 
	* They also serve to reduce the amount of information that any part of the system has to keep track of. 
	* They can be taken apart, and the subsystems formed can still function in their own right. 
	* When a system breaks down, it splits along its subsystem hierarchies. Thus, a reductionist point of view has merits in system science (although remember that subsystems also interact with each other)
	* *When a subsystem’s goals dominate at the expense of the total system’s goals, the resulting behavior is called* **suboptimization** [^1]. Of course, there is a [[Trade Offs|balance that must be struck]] between centralized and decentralized approaches
	* Hierarchical systems evolve from the bottom up. The purpose of the upper layers is to serve the purposes of the lower layers. 

[^1]: In other words, it is [[Game Theory - Strategy#Solving Games|not Pareto optimal]]

# Systems as Models 
* Systems are [[The Psychopathology of Everyday Things|conceptual models]] for the world around us. They usually have a strong congruence with the world. However, they often fall short of [[False Priors and Extension Neglect|representing]] the world fully
	* Systems fool us by presenting themselves as a series of events.
	* We are less likely to be surprised if we see how events accumulate into dynamic patterns of behavior.
	* *Behavior based models are more useful than event based ones* because they facilitate understanding of the underlying systems and have more predictive power. However, there are a few pitfalls 
		* They overemphasize flows and underemphasize stocks. 
		* In trying to find statistical links that relate flows to each other, we are trying to find something that does not exist. 
		* The predictive power of such models are better for short-term rather than long-term performance. 

* *Systems feature non-linear relationships* These nonlinearities make systems more difficult to understand. 
	* These non-linearities can also change the relative strengths of the feedback loops. 
	* *Non-linearities can cause dominance shifts among the feedback loops of the system.*.

* *Systems rarely have boundaries*. They rarely exist within a closed system.
	* Systems as models simplify this by delineating a system in study with other systems that very likely do not influence the system in a significant way based on what is being studied.
	* In the end, there is no single legitimate boundary that can be drawn around a system. 
	* Too narrow of a boundary can lead to surprises as external variables that do influence the system are not included in the model.
	* Too large of a boundary results in complicated analyses. 
	* [[Framing Effect]] applies in this case as we may be prone to setting the boundaries based on existing boundaries.

* *In systems, many causes can produce many effects* Any physical entity with multiple inputs and outputs is surrounded by layers of limits. 
	* At any given time, the input that is most important to a system is one that is most limiting. 
	* Changes in limiting factors tend to be the most impactful. 
	* As the system evolves, the input that is limiting also changes. One factor may become limiting or non-limiting in the future. 
	* *There will always be limits to growth.* They can be self-imposed. If they aren't they will be system imposed. 

* *Systems always feature delay*. It is surprising how long things change in a system. Stocks are delays, and most flows have delays. 
	* It is important to consider the scale of the delays that are important. Consider delays at the right level of granularity. 
	* When there are long delays in feedback loops, *some sort of foresight is essential*. To act only when a problem becomes obvious is to miss an important opportunity to solve the system. 

* *Human-based systems typically feature bounded rationality*. People act in their best interests based on the information they have even if it is to society's detriment. 
	* Perfect information is rarely present in a system. 
	* We have our own share of faulty [[Human Biases|biases]] which render it difficult to act rationally. 
	* One remedy to bounded rationality is to introduce more information. 
	* The right [[Knowing What To Do -- Constraints, Discoverability and Feedback|feedback]] also helps actors behave rationally as they impose corrective behavior. Incentives and constraints also help. 

# Links 
* [[System Dynamics]]
* [[Thinking in Systems by Meadows]] - Ch. 3 - 4
* [[Principles of Systems Science by Mobus and Kalton]] - Ch. 1 - 3