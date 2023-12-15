---
aliases:
  - game
---

* A **game** is a [[Characterizing the Decision Problem|decision process]] which involves multiple players that affect the environment and each other. 

# Games 
* A **finite game** is a game with a finite number of players in which the number of strategies is finite for all players . 

## Static Games
* A **static game** is a game where players simultaneously and independently make a once and for all decision, after which all outcomes are realized and payoffs are distributed to each player. 

* The **normal-form game** is a tuple $(N,S,v)$
	* A finite set of players $N = \{1,\dots, n\}$ 
	* A set of actions for each player $S=\{S_1, \dots, S_n\}$
	* A set of payoff functions $v=\{v_1,\dots, v_n\}$ for each player that gives a payoff vale to each  combination of the players' chosen actions.  They are functions $v_i:S_1\times S_2\times\dots\times S_n \to \mathbb{R}$

* Any 2-player finite normal-form game can be represented as a matrix where 
	* *Rows* represent one player 1's strategies.  
	* *Columns* represent one of  2's strategies 
	* Entries represent a two element vector $(v_1,v_2)$ representing the players' payoffs. 

## Dynamic Games
* A **dynamic game** is a game where players take turns and make a decision, potentially based on the choices of other players. 

* An **extensive-from game** is a tuple $\Gamma = (\mathcal{K}, \mathbb{H}, \{H_i\}, \{A(H)\}, a, \rho, v)$ where 
	* Let $D = V-Z$ represent the decision nodes 
	* $\mathcal{K}=(V,v_0,Z,p)$ is a finite [[Trees|tree]] called the **game tree** with vertices $V$, a unique initial node $v^0\in V$, a set of terminal nodes $Z\subset V$. and an immediate predecessor function $p:V\to D$ on which the game rules are represented.  
	* $\mathbb{H}$ is a partition on $D$ called the **information partition**. 
		* The information partition consists of information sets $h_i\in H_i$ which *partition the nodes of the game* at which player $i$ moves with the player properties. 
			* If $h_i$ is singleton, that includes only $x$, then player $i$ who moves at $x$ knows he is at $x$
			* If $x\ne x'$ and both $x\in h_i$ and $x'\in h_i$, then player $i$ who moves at $x$ does not know whether he is at $x$ or $x'$, and $A_i(x')=A_i(x)$. 
		* The restriction $A_i(x')= A_i(x)$ hides any information that can be distinguished about the player's current state on the board. 

 * $A(H)$ is a set of actions available for each information set $H\in\mathbb{H}$ which forms a partition over all actions $\mathcal{A}$. 
* $a:V-\{v^0\}\to \mathcal{A}$ is an action partition associating each node $v$ to a single action $a(v)$ such that $\forall H\in \mathbb{H}, \forall v\in H$, and where $s(v)$ denotes the successor nodes of $v$, $a_v: s(v)\to A(H)$ is a bijection
* $N$ is the set of players. $0$ denotes the player Nature who is independent of the [[Game Theory - Strategy|strategy]] of the players. 
* $\rho$ is a family of probabilities $\rho_H$ of the actions of Nature 
* $v=(v_i)_{i\in N} : Z\to \mathbb{R}^N$ denotes the payoff profile function 


* A potentially small set of moves can translate into a *much larger set of strategies* when sequential moves are possible, and when players have knowledge of what preceded their play

* *Any extensive-form game can be transformed into a normal-form game* by using the set of pure strategies of the extensive form as the set of pure strategies in the normal form and the set of payoff functions is derived from how combinations of pure strategies result in the selection of terminal nodes
	* The pure strategies are represented as follows (for two player games). Let the actions be ordered $\{a_1,\dots, a_m\}$.  Say player 1 has an entry $b_1,\dots, b_m$ where
		* $b_i\in \mathcal{A}$.  The $b_i$'s need not be distinct 
		* $b_k$ denotes that player 1 plays action $b_k$ in response to player $2$ playing $a_k$

## Multistage Games
* A **multistage game** is a finite sequence of normal-form **stage games** in which each stage-game is an independent, well-defined game of complete but imperfect information. The games are played sequentially by players and the total payoffs are evaluated using the sequence of outcomes in the game.
	* *Assume*: Each stage game takes place in a single time step. 
	* *Assume*: After each stage is completed, all players observe the outcome of the stage and the information structure is common knowledge.

* The total payoff is calculated as a [[Characterizing the Decision Problem|discounted sum]] of payoffs.
* The game can be represented using a game tree 
* Each information set is associated with the history of play from previous stage games 

## Repeated Game 
* Given a stage game $G$, $G(T,\gamma)$ denotes a **finitely repeated game** in which the stage game $G$ is played $T$ times with $\gamma$ as the common discount factor.

* For an **infinitely repeated game**, denoted $G(\gamma)$ we can define the following for discount factor $0<\gamma < 1$. 
  
  The **present value** given payoffs $\{v_i^t\}_{t=1}^\infty$ is given as 
  
  $$
  v_i = \sum_{t=1}^\infty \gamma ^{t-1}v_i^t
  $$
	* In this context, *we can interpret discounting as a response to an uncertain future* -- there is a probability $\gamma$ that the game will halt. 
	* The game is, therefore, infinite in the sense that it is unclear how long the foreseeable future is. 

* The **average payoff** of the given payoffs $\{v_i^t\}_{t=1}^\infty$ is 
  
  $$
  \overline{v}_t = (1-\gamma) \sum_{t=1}^\infty \gamma^{t-1} v_i^t
  $$

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

* **Games of Incomplete Information** are games where the players have belief for the other player's types but these beliefs are not certain. 
	* The set of each players and their possible actions are common knowledge. 
	* Each player may be associated with one of possibly many payoff functions (each payoff function denotes a type). 
	* At the beginning of the game, Nature chooses each player's type from a probability distribution. 
	* Each player is assumed to know their preferences 
	* **Common Prior Assumption** The probability distribution over types is common knowledge among the players. 

## Recall 
* **Games of Perfect Recall** are those where no player ever forgets information they previously knew .

* Under games of perfect recall, Mixed Strategies and Behavioral Strategies are equivalent. 
	* A mixed strategy can be obtained from a behavioral strategy by conditioning on the information set.
	* A behavioral strategy can be obtained from a mixed strategy by "un-conditioning" on the information set. 

* *Stochastic environments (where the dynamics of the environment change) are games where perfect recall is impossible.*

# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 3]]