* Generalizes [[Static Games of Incomplete Information#Bayesian Games|Bayesian Games]] to an [[Game Theory - Games|Extensive-form]] setting. 
* The usual solution concept of subgame-perfect equilibrium may have no bite for games with incomplete information. *When there is incomplete information, the only actual subgame is often the whole game.* which means it is no different from using the [[Static Games of Complete Information|Nash Equilibrium]] for analysis. 
	* Hence, the players do not have an idea of their current state and act as if they are stateless 

# Redefining Sequential Rationality
## Perfect Bayesian Equilibrium 
* We wish to induce [[Dynamic Games of Complete Information#Sequential Rationality|sequential rationality]] but at every information set. 
* Let $\sigma^\ast$ be a Bayesian Nash equilibrium profile of strategies in a game of incomplete information.
  
  An information set is **on the equilibrium path** if given $\sigma^\ast$ and the distribution of types, it is reached with positive probability.
  
  Otherwise, it is **off the equilibrium path** if it is reached with $0$ probability.

* A **system of beliefs** $\mu$ of an extensive form game assigns a [[Random Variables and Probability Distributions|probability distribution]] over decision nodes to every information set. 
	* We may have **endogenous** constraints that are determined from the behavior of other players. 
	* We may also have **exogenous** constraints that are determined from the choices of Nature through the type distribution.

* In order to have sequential  rationality in games of incomplete information, we require the following 
	* Every player will have a *well-defined belief* over where he is in each of his information set. 
	* *Ever player's beliefs are correct in information sets that are reached with positive probability*. More formally. 
	  
	  Let $\sigma^\ast$ be a Bayesian Nash equilibrium profile of strategies. In in all information sets beliefs that are on the equilibrium path are consistent with Bayes' rule.  
		* That is, the beliefs incorporate both endogenous  and exogenous constraints 
		* The beliefs are based on the player types [[Bayesian Statistics|conditional]] on the opponents playing a certain strategy. That is, $\mu(\theta \mid s)$. 
	* *Bayes rule does not apply to information sets off the equilibrium path*. Beliefs in this case are arbitrary and unconstrained. 
	* Given their beliefs, players' strategies must be sequentially rational. That is, in every information set, *players will play a best response in their beliefs*.
	  
	  More formally, if $h$ is an information set for player $i$, then it must be true that he is playing a strategy $\sigma_i$ that satisfies $\forall s'_i \in S_i$
	  
	  $$
	  \mathbb{E} \left[ \ v(\sigma_i, \sigma_{-i}, \theta_i ) \mid h,\mu \right ] \ge \mathbb{E} \left[ v_i (s',\sigma_{-i}, \theta_i ) \mid h,\mu\right] 
	  $$
	  Where expectation is over the beliefs of player $i$ using $\mu$. 

* A Bayesian Nash equilibrium profile $\sigma^\ast$ and a system of beliefs $\mu$ constitutes a **(weak) perfect Bayesian equilibrium** if it satisfies the four requirements above. 

* (*Tadelis 15.1*) If a profile of possibly mixed strategies $\sigma^\ast$ is a Bayesian Nash equilibrium of a Bayesian game $\Gamma$ and if $\sigma^\ast$ induces all information sets to be reached with positive probability, then $\sigma^\ast$, and $\mu^\ast$ uniquely derived from $\sigma^\ast$ and the distribution of types constitutes a perfect Bayesian equilibrium for $\Gamma$. 
	* If a game has a Bayesian Nash equilibrium that has all the information sets being reached on the equilibrium path, then *beliefs will be uniquely pinned down by Bayes' rule*. 

## Sequential Equilibrium 
* There are games where the perfect Bayesian equilibrium allows for equilibria that seem unreasonable because *there is no restriction on the beliefs that are off the equilibrium path*

* A profile of strategies $\sigma^\ast$ and system of beliefs $\mu^\ast$ is **consistent** if there exists a sequence of nondegenerate (that is, the strategies aren't pure) mixed strategies $\{\sigma^k\}_{k=1}^\infty$ and a sequence of beliefs that are derived from each $\sigma^k$ according to Bayes' rule $\{\mu^k\}_{k=1}^\infty$  such that 
  
  $$
  \lim_{k\to\infty} (\sigma^k,\mu^k) = (\sigma^\ast, \mu ^\ast)
  $$
  
* A profile of strategies $\sigma^\ast$ and a system of beliefs $\mu^\ast$ is a **sequential equilibrium** if $(\sigma^\ast, \mu^\ast)$ is a consistent perfect Bayesian equilibrium.

# Signaling Games 
* Games which feature the following:
	* Nature chooses a type for player $i$ that the other players do no not know but cares about (as common values)
	* Player $i$ has a rich action set in the sense there are at least as many actions as types and each action imposes a different cost on each type.
	* Player $i$ chooses an action first and the other players respond by observing the choice.
	* Given the other players' belief about player $i$'s strategy, the other players update their beliefs after observing player $i$'s choice. The other players then make their choice as a best response to the updated beliefs . 
* *The other players learn the type of player $i$ through their actions*. 

* These games have two classes of perfect Bayesian equilibria 
	* **Pooling equilibria** - all types of player $i$ choose the same action, revealing nothing to other players.
		* The opponents have beliefs about all the information sets. 
		* A sequentially rational strategy of the opponent given their beliefs prevents player $i$ from deviating from the pooling strategy. 
	* **Separating equilibria** - each type of player $i$ chooses a different action, revealing the type in equilibrium to the other players. 
		* The opponent must have beliefs about the actions of the other types (in those that are off equilibrium) 
		* A sequentially rational strategy of the opponent supports the separating strategy. 
	* **Semi-Separating / Hybrid equilibria** - different types choose mixed strategies. 
		* Some information sets that belong to the uninformed player can be reached by different types with different probabilities. 
		* The opponent can learn something about the player but cannot always infer exactly which type they are. 

# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 16 - 18]]
* [[Game Theory - Strategy]]