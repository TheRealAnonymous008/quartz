* Neuroevolution has implications in both [[Artificial Intelligence]] and [[Psychology]].

* [^Bahceci_2023] examines how strategies can be evolved for use in Competitive Multi-Agent Search (CMAS). It develops CMAS as a *formalization of human problem solving*.
	* The CMAS framework has the following properties.
		* It is modeled as a search for the same highest peaks in a common fitness landscape.
		* Agents can have private information about their own searches; Alternatively, they can also make information public to other agents.
		* Search actions have an effect on the landscape that is visible to all agents. 
		* The agents' search strategies are stochastic, representing the bounded rationality of real-world agents 
	* The formalization also makes it possible to use such models to determine how humans could perform better than they currently do.
	* It makes use of NEAT as the neuroevolutionary approach that produces strategy patterns, and [[Agent Based Modeling]] to model interactions between agents. 
	* Agents can employ two search strategies. 
		* The $S_1$ search strategy involves either  [[The Exploitation-Exploration Trade-Off|exploring or exploiting]] using either the public or private memory. It may be formalized as 
			* Exploiting starts with a given point in the search space and tries to find new high fitness points in its neighborhood.
			* Exploring starts with a given point in the search space  and tries to find new high fitness points not in its neighborhood. 
		* The $S_2$ strategy determines where to put a newly discovered point (either in public or private memory) depending on the fitness of the point.
		* Search strategies are represented using a Compositional Pattern Producing Network (CPPN) .
	* Distinctly different search strategies evolve in different environments. These strategies tend to be better than strategies evolved in the environment, general strategies, and handcrafted strategies. These strategies also tend to be more complex.

![[CMAS.png]]
<figcaption> CMAS Simulation Algorithm. Image taken from Bahceci, Katilla and Mikkulainen (2023) </figcaption>



[^Bahceci_2023]:: Bahceci, Katila, and Mikkulainen (2023) [Evolving Strategies for Competitive Multi-Agent Search](https://arxiv.org/abs/2306.10640)


# Links
* [[Metaheuristics]]
