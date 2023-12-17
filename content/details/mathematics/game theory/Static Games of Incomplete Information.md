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
 \mathbb{E}_{\theta_{-i}} \ \bigg[ \phi_i (\theta_{-i}\mid \theta_i) \   v_i(s_i^\ast (\theta_i )  \ , s_{-i}^\ast (\theta_i) \ ; \theta_i) \mid \theta_i \bigg] \ge \mathbb{E}_{\theta_{-i}} \bigg[v_i(a_i,s_{-i}^\ast (\theta_{-i}); \theta_i) \mid \theta_i\bigg] 
  $$

* **Harsayani's Purification Theorem** - we can use incomplete information to make any mixed-strategy equilibrium of a game of complete information into a pure strategy. 
	* If people are somewhat heterogeneous in the way monetary payoffs and actions are related, then we can have uncertainty over the types of players who are playing pure strategies, but *the distribution of types makes a player have beliefs as if he were facing a player who is playing a mixed strategy*
	* Thus, games of complete information are in some sense a special case of games of incomplete information where players have strict best responses. 
# Applications 
* (*Tadelis 12.1*) . Trade can only occur in a Bayesian Nash equilibrium only if it involves the lowest type trading.
	* The intuition is that a player (who knows the value of the trading object) will only give it away if they know it has low value.  
	* The end result is trade can only occur if the quality of the object being traded is at its lowest. 

* The **swing voter's curse**. When a voter believes their vote matters, they must condition this on the situation which his vote counts. But then it means that they will interpret their information differently and not use it in an unbiased way

* [[Auction Theory]]
* [[Mechanism Design]]

# Links
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 12]]
	* 12.2  - 12.4- contains examples in greater detail. 
* [[Game Theory - Games]]
* [[Game Theory - Strategy]]