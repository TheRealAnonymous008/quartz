* A **metaheuristic** is a heuristic designed to find or select a heuristic that gives a "good enough" solution to an optimization problem, especially applicable for [[Complexity Theory|NP hard]] problems.
* *Metaheuristics are generally applicable, but do not guarantee optimality or polynomial running time*

* For each heuristic, let $f$ be the function being optimized. $x$ is an element in the solution space of the problem. 

# Metropolis-Hastings Algorithm
* The **Metropolis-Hastings Algorithm** is a Monte Carlo method for generating random samples from a [[Random Variables and Probability Distributions|probability distribution]] $P(x)$ whose distribution is difficult to compute.
* The goal is to construct a [[Markov Chain|Markov Process]] that simulates the behavior of $P(x)$ -- it has the same stationary behavior as $P(x)$.

```
g(x'|x) : = distribution giving the probability of generating x' given x

t = 0
x_0 := initial solution chosen

loop:
	Generate x'~ g(x' | x)

	Calculate the acceptance probability (defined below)

	Accept or reject based on the acceptance probability.
	if accept:
		x_{t+1} = x'
	else: 
		x_{t+1} = x_t
	t =  t + 1

```

* The acceptance probability $A(x', x_t)$ is defined as follows

$$
A(x',x_t) = \min\left( 1, \frac{P(x') g(x_t\mid x')}{P(x_t) g(x'\mid x_t)}\right)
$$


# Simulated Annealing
* Inspired by the annealing process in metallurgy where metals are heated and cooled to improve strength.
* We introduce the following
	* A cost function $c$ that determines the cost of $x$. 
	* A temperature hyperparameter $T$ in the same units as the cost function
	* A neighborhood of $x$, denoted $N(x)$. We sample from this neighborhood, denoted $x\sim N(x)$. 
	* A convergence criterion. 
	* A cooling schedule $\mathcal{T}(t)$ which determines the temperature at time $t$. 

```
t = 0
x_0 := initial solution
x* := optimal solution found so far. Initialize as x_0

while covnergence criterion not met:
	Genenrate x' ~ N(x)
	Get temperature T from cooling schedule at time t.

	Calculate acceptance probability (see below)

	if accept:
		x* = x'
	else: 
		x* = x_t

	t = t + 1

return x*
```

* The acceptance probability is defined as 
  $$
  A(x',x^\ast) = \min\left({1, \exp\left(-{\frac{c(x')-c(x^\ast)}{k_BT}}\right)}\right)
  $$
  
  Where $k_b$ is the Boltzmann constant.

* The behavior of the above function is that of a [[Probability Distributions Zoo|Boltzmann distribution]], mimicking the behavior of particles in thermodynamic equilibrium.

# Animal-Inspired Search
* [^xue_2020] propose a new [[Swarm Intelligence|swarm]] optimization approach called **sparrow swarm search** inspired by group wisdom, foraging and anti-predation observed in sparrows.  Sparrows have two classes -- producers and scroungers. Sparrows follow the following rules
	* Producers have high energy reserves. The level of energy reserves depends on the assessment of fitness values of the individuals.
	* Sparrows detect predators and send an alarm. When the alarm is strong enough, producers lead all scroungers to a safe area.
	* Each sparrow can become a producer as long as it searches for the better food sources, but the proportion of the producers and the scroungers is unchanged in the whole population
	* Sparrows with higher energy are producers. Starving scroungers fly to other places for food to get more energy.
	* The scroungers follow the producer who can provide the best food to search for food.
	* The sparrows at the edge of the group quickly move toward the safe area to get a better position when aware of danger, while the sparrows in the middle of the group randomly walk in order to be close to others.

![[Sparrow Swarm Search.png]]
<figcaption> Sparrow Swarm Search Algorithm from Xue and Shen (2020) </figcaption>

[^Xue_2020]: Xue and Shen (2020) [A novel swarm intelligence optimization approach: sparrow search algorithm](https://www.tandfonline.com/doi/pdf/10.1080/21642583.2019.1708830)


# Links
* [Metaheuristics](https://en.wikipedia.org/wiki/Table_of_metaheuristics)