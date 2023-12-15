* The idea is largely similar to [[Static Games of Complete Information]] except now each player has to respond to each type of player, not unlike a [[Dynamic Games of Complete Information|Game of imperfect information]].
	* We can still use the usual game matrix, except each row and column denotes a combination of prescribed actions against each type. 
	  
	  More formally if $t_1,\dots,t_k$ are the set of types, then each row (for player $i$) corresponds to $a_1, a_2,\dots, a_K$ where $a_j$ is the action taken when the player type is $t_j$.

# Bayesian Games 
* The normal-form representation of an $n$-player **static Bayesian Game of Incomplete Information** is specified with a tuple $(N, \ A, \ \Theta, \ v, \ \phi )$
  
  Where
  $N=\{1,\dots, n\}$ is the set of players. 
  $A=\{A_1,\dots,A_n\}$ is the set of actions. $A_i$ is the action of the $i$-th player. Let
  $\mathbb{A}=A_1\times \dots \times A_n$ 
  $\Theta=\{\Theta_1,\dots,\Theta_n\}$ - the set of type spaces 
  $\Theta_i=\{\theta_{i1},\dots,\theta_{ik_i}\}$ - the type space of player $i$ 
  $v=\{v_1,\dots, v_n\}$ - the set of value functions of the players  
  $v_i : \mathbb{A} \times \Theta_i \to \mathbb{R}$ - is the $i$-th value function. 
  $\phi=\{\phi_1,\dots,\phi_n\}$ - is the set of belief. Each function is of the [[Bayesian Statistics|form]] $\phi_i(\theta_{-i}\mid\theta_i)$ 


* The Bayesian game as one that proceeds as follows:
	* Nature chooses a profile of types $\theta=(\theta_1,\dots,\theta_n)$
	* Each player $i$ learns his own type $\theta_i$ which is his **private information** and then uses his prior $\phi_i$ to form posterior beliefs over the other types of players. 
	* Players simultaneously choose actions $a_i\in A_i$ (as in the static game).
	* The payoffs $v_i(a \mid \theta_i)$ are realized using the action profile $a=(a_1,a_2,\dots, a_n)$. 

* The **private values** case will assume that $v_i$ depends only on the private information. In the **common values** case, we will assume $v_i (a \ ;  \ \theta)$ wherein the payoff depends on the other player types.

* A **pure strategy** for player $i$ is a function $s_i:\Theta_i \to A_i$ that prescribes a pure action $s_i(\theta_i)$ that player $i$ will choose when his type is $\theta_i$. A **mixed strategy** is a [[Random Variables and Probability Distributions|probability distribution]] over a player's pure strategies. 
	* *Each player chooses his type-contingent strategy before he learns his type*.
	* In effect, each player views the others as always choosing a mixed strategy. 

* A strategy profile $s^\ast$ is a **pure strategy Bayesian Nash Equilibrium** if, for every player $i$, for each of player $i$'s types $\theta_i\in \Theta_i$ and for each $a_i\in A$, $s_i^\ast$ solves 
  
  $$
 \mathbb{E}_{\theta_{-i}} \ [ \phi_i (\theta_{-i}\mid \theta_i) \   v_i(s_i^\ast (\theta_i )  \ , s_{-1}^\ast (\theta_i) \ ; \theta_i) \mid \theta_i ] \ge \mathbb{E}_{\theta_{-i}} [v_i(a_i,s_{-i}^\ast (\theta_{-i}); \theta_i) \mid \theta_i] 
  $$

# Example Games 

# Links
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 12 - 14]]
	* 12.2 - contains examples: Chicken and Study Groups.
* [[Game Theory - Games]]
* [[Game Theory - Strategy]]