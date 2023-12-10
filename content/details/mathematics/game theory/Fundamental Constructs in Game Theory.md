* A **game** is a [[Characterizing the Decision Problem|decision process]] which involves multiple players that affect the environment and each other. 

# Games 
* A **finite game** is a game with a finite number of players in which the number of strategies is finite for all players . 

### Static Games
* A **static game** is a game where players simultaneously and independently make a once and for all decision, after which all outcomes are realized and payoffs are distributed to each player. 

* The **normal-form game** is a tuple $(N,S,v)$
	* A finite set of players $N = \{1,\dots, n\}$ 
	* A set of actions for each player $S=\{S_1, \dots, S_n\}$
	* A set of payoff functions $v=\{v_1,\dots, v_n\}$ for each player that gives a payoff vale to each  combination of the players' chosen actions.  They are functions $v_i:S_1\times S_2\times\dots\times S_n \to \mathbb{R}$

* Any 2-player finite normal-form game can be represented as a matrix where 
	* *Rows* represent one player 1's strategies.  
	* *Columns* represent one of  2's strategies 
	* Entries represent a two element vector $(v_1,v_2)$ representing the players' payoffs. 

### Dynamic Games
* A **dynamic game** is a game where players take turns and make a decision, potentially based on the choices of other players. 

* An **extensive-from game** is a tuple $\Gamma = (\mathcal{K}, \mathbb{H}, \{H_i\}, \{A(H)\}, a, \rho, v)$ where 
	* Let $D = V-T$ represent the decision nodes 
	* $\mathcal{K}=(V,v_0,T,p)$ is a finite [[Trees|tree]] with vertices $V$, a unique initial node $v^0\in V$, a set of terminal nodes $T\subset V$. and an immediate predecessor function $p:V\to D$ on which the game rules are represented.  
	* $\mathbb{H}$ is a partition on $D$ called the **information partition**. 
		* The information partition consists of information sets $h_i\in H_i$ which *partition the nodes of the game* at which player $i$ moves with the player properties. 
			* If $h_i$ is singleton, that includes only $x$, then player $i$ who moves at $x$ knows he is at $x$
			* If $x\ne x'$ and both $x\in h_i$ and $x'\in h_i$, then player $i$ who moves at $x$ does not know whether he is at $x$ or $x'$, and $A_i(x')=A_i(x)$. 
		* The restriction $A_i(x')= A_i(x)$ hides any information that can be distinguished about the player's current state on the board. 

 * $A(H)$ is a set of actions available for each information set $H\in\mathbb{H}$ which forms a partition over all actions $\mathcal{A}$. 
* $a:V-\{v^0\}\to \mathcal{A}$ is an action partition associating each node $v$ to a single action $a(v)$ such that $\forall H\in \mathbb{H}, \forall v\in H$, and where $s(v)$ denotes the successor nodes of $v$, $a_v: s(v)\to A(H)$ is a bijection
* $N$ is the set of players. $0$ denotes the player Nature who is independent of the strategies of the players. 
* $\rho$ is a family of probabilities $\rho_H$ of the actions of Nature 
* $v=(v_i)_{i\in\mathcal{I}} : T\to \mathbb{R}^N$ denotes the payoff profile function 


* A potentially small set of moves can translate into a *much larger set of strategies* when sequential moves are possible, and when players have knowledge of what preceded their play

* *Any extensive-form game can be transformed into a normal-form game* by using the set of pure strategies of the extensive form as the set of pure strategies in the normal form and the set of payoff functions is derived from how combinations of pure strategies result in the selection of terminal nodes
	* The pure strategies are represented as follows (for two player games). Let the actions be ordered $\{a_1,\dots, a_m\}$.  Say player 1 has an entry $b_1,\dots, b_m$ where
		* $b_i\in \mathcal{A}$.  The $b_i$'s need not be distinct 
		* $b_k$ denotes that player 1 plays action $b_k$ in response to player $2$ playing $a_k$
# Information
* An event $E$ is **common knowledge** if:
	* Everyone knows $E$ 
	* Everyone knows that everyone knows $E$ ad infinitum
 * *Common knowledge allows a strategic framework* because we know that everyone will act according to their [[Bayesian Statistics|belief]] that everyone else has the common knowledge. 

* **Games of Complete Information** require the following for components to be common knowledge among all players of the game 
	* All possible actions of all the players 
	* All the possible outcomes 
	* How each combination of actions of all players affect which outcome will materialize 
	* The preferences of each and every player over outcomes. 

* **Games of Perfect Information** are games of complete information where every information set is singleton, and there are no moves of Nature.  
* **Games of Imperfect Information** are games where some information sets contain several nodes or where there are moves of nature. 
	* These are games capture two kinds of uncertainty. **Exogenous uncertainty** - comes from not knowing the move of another player. **Endogenous uncertainty** - comes from not knowing the realization of a choice of Nature. 

## Recall 
* **Games of Perfect Recall** are those where no player ever forgets information they previously knew .

* Under games of perfect recall, [[#Mixed Strategies]] and [[#Behavioral Strategies]] are equivalent. 
	* A mixed strategy can be obtained from a behavioral strategy by conditioning on the information set.
	* A behavioral strategy can be obtained from a mixed strategy by "un-conditioning" on the information set. 

* *Stochastic environments (where the dynamics of the environment change) are games where perfect recall is impossible.*

# Strategies 
* A **pure strategy** for player $i$ is a *deterministic plan of action*. The set of all pure strategies of player $i$ is denoted $S_i$.
	* Strategies are distinct from actions. The outcomes may be conditioned on the choice of actions but not the strategy. 
	* *In an extensive-form game*, the strategy also describes what player $i$ will choose at each of his information sets $h_i \in H_i$. 
	  
	  More formally, it is a mapping $s_i : H_i \to A_i$ that assigns action $s_i(h_i)\in A_i(h_i)$ for every information set $h_i \in H_i$. 
  
  A **profile of pure strategies**, $s=(s_1,\dots, s_n)$ describes a particular combination of pure strategies chosen by all $n$ players of the game 

* The **simplex** of $S_i$, denoted $\Delta S_i$. is the set of all  [[Random Variables and Probability Distributions|Probability distributions]] over $S_i$. 

## Incorporating Beliefs 
* A strategy $s_i\in S_i$ is player $i$'s **best response** to his opponents' strategies $s_{-i}$ if 
  
  $$
  v_i(s_i,s_{-i}) \ge v(s_i', s_{-i}) \ \ \ \ \ \forall s_i'\in S_i
  $$
* A rational player who believes his opponents are playing some $s_{-i}$ will always choose a best response to $s_{-i}$. 

* A **belief** of player $i$ is a possible profile of his opponents' strategies $s_{-i}\in S_{-i}$. More formally , it is given by a probability distribution $\pi_i\in \Delta S_{-i}$.  $\pi_i(s_{-i})$ is the belief of player $i$ corresponding to their opponents playing $s_{-i}$.
* The **best response correspondence** of player $i$, selects for each $s_i\in S_{-i}$ a subset $\text{BR}_i (s_{-i})\subseteq S_i$ where each strategy $s_i\in \text{BR}_i(s_{-i})$ is a best response to $s_{-i}$ based on the player's beliefs.
* A strategy $s_i\in S$ is **never a best response** if there are no beliefs $s_{-i}\in S_{-i}$ for player $i$ for which $s_i\in \text{BR}_i(s_{-i})$

## Mixed Strategies 
* A **mixed strategy** for player $i$ is defined as $\sigma_i \in \Delta S_i$ where we have a probability distribution 
  
  $$
  \sigma_i = \{\sigma_i(s_{i1}),\dots, \sigma_i(s_{im})\}
  $$
  
  Where $\sigma_i(s_i)$ is the probability that player $i$ plays $s_i$.
  
  In other words, *a mixed strategy is simply a distribution over pure strategies.*

* Given a mixed strategy $\sigma_i(\cdot)$, we say that $s_i\in S_i$ is **in the support** of $\sigma_i(\cdot)$ if and only if it occurs with positive probability. That is $\sigma_i(s_i)>0$.

* For continuous settings, the simplex is an interval, the mixed strategy is a cumulative distribution function, and the support is the set of $s_i$ where the density function $f_i$ is positive. That is $f_i(s_i)>0$

* The **expected payoff** is given as follows: [^EP]
  
  $$
  \overline{v_i}(\sigma_i,\sigma_{-i}) = \sum_{s_i\in S_i}\left(\sum_{s_{-i}\in s_{-i}} \sigma_i(s_i )\ \sigma_{-i}(s_{-i}) \ v_i(s_i,s_{-i})\right)
  $$
  
  This degenerates when $\sigma_i$ is a pure strategy 
  
  $$
  v_i(s_i,\sigma_{-i}) = \sum_{s_{-i}\in S_{-i}} \sigma_{-i}(s_{-i}) \ v_i(s_i, s_{-i})
  $$

[^EP]: As usual, we give the discrete definition. For the continuous case, simply replace sums with integrals. 


* *If a player is mixing between several strategies, he must be indifferent between them*.  Hence, for mixed strategies, we can check which opponent strategies causes the player to be indifferent.
	* This follows from the fact that suppose the player weren't indifferent, then clearly one strategy must be better than the other in which case it is more optimal to simply not mix.
	* Indifference means that the expected utility from choosing either strategy is the same. 

## Behavioral Strategies 
* A **behavioral strategy** specifies for each information set $h_i \in H_i$ an independent probability distribution over $A_i(h_i)$ and is denoted $\sigma: H_i\to \Delta A_i(h_i)$, where $\sigma_i(a_i(h_i))$ is the probability that player $i$ plays action $a_i(h_i)\in A_i(h_i)$ in information set $h_i$/

* It generalizes [[#Mixed Strategies]] form extensive-form games by *allowing players to not only randomize between a choice of overall strategy, but randomize the strategy taken at each turn. *

## Substitutes and Complements 
* A game with **strategic substitutes** is a game where the best response of one player decreases in the choice of the other.  That is, *they mutually reinforce each other*. 
* A game with **strategic complements** is a game where the best response of one player increases the choice of the other. That is *they mutually offset one another*. 

# Solving Games 
* A **solution concept** is a method of analyzing games with the objective of restricting the set of all possible outcomes to those that are more reasonable than others. It is a formal rule for predicting how the game will play. 
	* *Solution concepts prescribe solutions. Solutions are strategies* 

* **Equilibrium** refers to a strategy profile that emerges as one of the solution concept's predictions. *It is the actual / likely predictions of our theory.*

* In analyzing equilibria, we assume the following: 
	* *Players are rational*. Players maximize payoff consistent with their beliefs about the game 
	* *Players are Intelligent*. They know everything about the game--actions, outcomes, and preferences of all players 
	* *Common knowledge* - the fact that players are rational and intelligent is common knowledge among all players .
	* *Self-enforcement* - any prediction or equilibrium of a solution concept must be self-enforcing. That is, *players engage in noncooperative behavior* -- players are happy with their own choices given how the others have made their own choices .

* We can analyze solution concepts by evaluating three things 
	* *Existence* - a solution concept must apply to a wide variety of games. It applies generally and we can show that it results in an equilibrium. 
	* *Uniqueness* - a solution concept must restrict the set of possible outcomes to a smaller set of reasonable outcomes. Ideally, we want a single unique outcome. 
	* *Invariance* - Slight perturbations in the payoff functions do not affect the predictions of a robust solution concept. 

* We may want solutions to games that are *socially desirable*. An outcome is **socially undesirable** if there is a better outcome that would make some people better off without harming anyone else.  *This is captured in Pareto optimality*. 

* A strategy profile $s\in S$ **Pareto dominates** strategy profile $s'\in S$ if
  $$
  \begin{split}
  \forall i \in N  \ \ \ \ & v_i(s) &\ge v_i(s')  \\ 
  \exists i \in N \ \ \ \ & v_i(s) &>  v_i(s') 
  \end{split}
  $$
  We say that $s'$ is **Pareto dominated** by $s$.
  
  A strategy profile is **Pareto optimal** if it is not Pareto dominated by any other strategy profile. 
	* *Pareto optimality does not necessarily leave all players equally happy*
	* Pareto optimality is not guaranteed in noncooperative settings. 
	* *In general, maximizing the sum of utility functions or maximizing total welfare will result in a Pareto optimal outcome*. However, it need not be the unique one. 


# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 3]]