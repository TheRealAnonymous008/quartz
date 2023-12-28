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

* For advantaged types to be able to separate themselves credibly from disadvantaged types there must be some signaling action that costs less for the advantaged types than it does for the disadvantaged types

* The **intuitive criterion** is a logical process defined as follows. For any given set of beliefs of the other players, player $i$ (who only has private information) can use their actions to send a message to this player in the spirit of *only an $x$ type would benefit from this move, therefore I am an $x$ type*. 
	* Take a perfect Bayesian equilibrium. If it does not survive the intuitive criterion, then it is ruled out. 

* More formally, consider a signaling game where player $i$ has private information $\theta\in \Theta$ and chooses actions $a_i\in A_i$ in the first period, after which player $j$ observes their action, forms a posterior belief over player $i$'s type and then chooses $a_j\in A_j$. 
	
	Let $\hat\Theta\subset \Theta$ be a subset of player $i$'s types. 
	Let $\text{BR}_j(\hat\Theta, a_i)$ be the set of  best response actions of player $j$ given that player $i$ has chosen $a_i$ and where belief $\mu$ assigns positive probability only to types in the set $\hat\Theta$ in a signaling game. 
	
	We have that 
	$$
	\text{BR}_j (\Theta,a_i)= \bigcup_{\mu\in \Delta(\Theta)} \underset{a_j\in A_j}{\text{argmax}} \sum_{\theta \in \hat{\Theta}} v_j(a_i,a_j \ ; \theta) \ \mu (\theta)
	$$

* A perfect Bayesian equilibrium $\theta^\ast$ **fails the intuitive criterion** if there exists $a_i\in A_i,\theta\in\Theta, \hat{\Theta}\subset \Theta$ such that 
	* $v_1 (\sigma^\ast; \theta) > \underset{a_2\in \text{BR}_2(\Theta,a_i)}{\text{max}} v_i(a_i,a_j \ \theta)$  $\forall \theta\in\hat{\Theta}$. That is, *any type in the subset $\hat{\Theta}$ would never choose to player $a_i$* because regardless of player $j$'s beliefs, he would do worse than if they stuck to equilibrium
	* $v_1 (\sigma^\ast; \theta) < \underset{a_2\in \text{BR}_2(\Theta-\hat{\Theta},a_i)}{\text{max}} v_i(a_i,a_j \ \theta)$. That is, *type $\theta$ will do better than the equilibrium by playing $a_i$ if they can properly signal*  -- they can convince player $j$ has their type is not $\hat{\Theta}$. 

# Reputation 
* If there is even just a little bit of incomplete information about the players’ types then for a long enough horizon of $T$ periods there can actually be quite a lot of cooperation.
* Consider the **Iterated Prisoner's Dilemma** where Player $1$ is one of two types -- strategic or grim-trigger. The grim trigger type will initially cooperate and continue to do so until the other player defects.  Let  $p$ denote the probability Nature chooses player $1$ to be the grim trigger type. 
* (*Tadelis 17.1*) Consider a $T$-period iterated Prisoner's Dilemma game in which $T$ is large. The number of periods in which either player $2$ or the strategic player $1$ defects is bounded above by a constant $M<T$ dependent on $p$ and not on $T$.

* In equilibrium models, players are, by definition, never fooled. However, if there is incomplete information, then *players will have rational uncertainty about whether players they face are set in their ways.*
	* Rational uncertainty can also be exploited by the players by mixing their strategies. 
	* This *gives rise to reputational incentive* since players can imitate behavioral types and trade-off short term benefit and optimality for long-term benefits. 
	* *This counteracts the grim trigger strategy*, especially when there is incomplete information and reputational incentives. This applies even with finite dynamic games.

# Information Transmission Games 
* Similar to [[#Signaling Games]], an **information transmission game** is one where player $i$ has private information and the payoffs exhibit common values so that all players depend on player $i$'s private information. However, *player $i$'s action is a message with no direct effect on payoff*.
* One player is referred to as the sender, and the other as the receiver. Game proceeds as follows 
	* Nature selects a type for the sender $\theta\in \Theta$ from common knowledge distribution $p$
	* Sender learns $\theta$ and chooses some message action $a_i\in A_i$ 
	* Receiver observes message $a_j$ and chooses $a_j\in A_j$ 
	* Payoffs $v_i(a_j,\theta)$ and $v_j(a_i,\theta)$ are realized.

* The inherent conflict of interest between the players will put *limits on how much information the informed player can credibly communicate* to the uninformed player in equilibrium.
* There are three key insights 
	* A fully truthful equilibrium (where the sender tells the truth) never exists 
	* A **babbling equilibrium** always exists, where the sender's message reveals no information and the receiver chooses an action to maximize their expected utility given their prior beliefs [^1]
	* If the sender's bias is not too large, then some information can be truthfully revealed in equilibrium. The small bias, rooted in the sender's personal interests, reduces the payoff gap in the receiver's choices.

* If the sender's information space is very large, then even a small amount of bias between their preferences and the receiver's preferences will result in some information not being revealed.

[^1]: So in Bayes' rule, the likelihood is set to $0$. We do not update our priors.
# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 15 - 18]]
	* Ch. 16 - more on signaling games 
	* Ch. 17 - more on building reputation (such as via the Iterated Prisoner's dilemma, Bargaining and the Centipede Game)
	* Ch. 18 - more on the application of cheap talk games to legislative organization.
* [[Game Theory - Strategy]]