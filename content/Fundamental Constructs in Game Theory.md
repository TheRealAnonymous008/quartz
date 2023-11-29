* A **game** is a [[Characterizing the Decision Problem|decision process]] which involves multiple players that affect the environment and each other. 

# Fundamentals 
* A **pure strategy** for player $i$ is a *deterministic plan of action*. The set of all pure strategies of player $i$ is denoted $S_i$.
	* Strategies are distinct from actions. The outcomes may be conditioned on the choice of actions but not the strategy. 
  
  A **profile of pure strategies**, $s=(s_1,\dots, s_n)$ describes a particular combination of pure strategies chosen by all $n$ players of the game 

* The **normal-form game** is a tuple $(N,S,v)$
	* A finite set of players $N = \{1,\dots, n\}$ 
	* A set of actions for each player $S=\{S_1, \dots, S_n\}$
	* A set of payoff functions $v=\{v_1,\dots, v_n\}$ for each player that gives a payoff vale to each  combination of the players' chosen actions.  They are functions $v_i:S_1\times S_2\times\dots\times S_n \to \mathbb{R}$

* A **finite game** is a game with a finite number of players in which the number of strategies is finite for all players . 
* Any 2-player finite game can be represented as a matrix where 
	* *Rows* represent one player 1's strategies.  
	* *Columns* represent one of  2's strategies 
	* Entries represent a two element vector $(v_1,v_2)$ representing the players' payoffs. 

## Incorporating Beliefs 
* A strategy $s_i\in S_i$ is player $i$'s **best response** to his opponents' strategies $s_{-i}$ if 
  
  $$
  v_i(s_i,s_{-i}) \ge v(s_i', s_{-i}) \ \ \ \ \ \forall s_i'\in S_i
  $$
* A rational player who believes his opponents are playing some $s_{-i}$ will always choose a best response to $s_{-i}$. 

* A **belief** of player $i$ is a possible profile of his opponents' strategies $s_{-i}\in S_{-i}$,
* The **best response correspondence** of player $i$, selects for each $s_i\in S_{-i}$ a subset $\text{BR}_i (s_{-i})\subseteq S_i$ where each strategy $s_i\in \text{BR}_i(s_{-i})$ is a best response to $s_{-i}$ based on the player's beliefs.
* A strategy $s_i\in S$ is **never a best response** if there are no beliefs $s_{-i}\in S_{-i}$ for player $i$ for which $s_i\in \text{BR}_i(s_{-i})$
# Static vs Dynamic 
* A **static game** is a game where players simultaneously and independently make a once and for all decision, after which all outcomes are realized and payoffs are distributed to each player. 


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


# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 3]]