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

## Multistage Conditional Strategies 
* In a [[Game Theory - Games#Multistage Games|multistage game]], a **pure strategy** of player $i$ will be a list of conditional pure strategies of the following form 
  $$
  S_i = \{s_i^1, s_i^2 (h_1), \dots, s_i^T(h_{T-1})
  $$
  where $h_{t-1}$ is a particular outcome that occurred up to period $t$, not including period $t$. It denotes the history of events that occurred up to $t$. 

* A **mixed behavioral strategy** is a list of conditional randomizations of the form $\sigma_i = \{\sigma_i^1,\dots, \sigma_i^T(h_{T-1})\}$ 

## Strategies for Infinitely Repeating Games
* Let $H_t$ denote the possible **histories** of length $t$ and $h_t\in H_t$.  
  Let $H=\cup_{t=1}^\infty H_t$ be the set of all possible histories .
  
  A **pure strategy** for player $i$ is a mapping $s_i : H\to S_i$. 
  A **behavioral strategy** for player $i$ is a mapping $\sigma_i: H\to \Delta S_i$ .

## Strategies in Incomplete Information Settings 
* A strategy in an incomplete information setting is a prescription on what each player should do in response to each type of player. 
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