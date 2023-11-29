# Strict Dominance  
* Let $s_i, s_i' \in S_i$ be possible strategies. $s_i'$ is **strictly dominated** by $s_i$ if, for any possible combination of other players' strategies $s_{-i}\in S_{-i}$ , player $i$'s payoff from $s_i'$ is strictly less than that from $s_i$. That is 
  
  $$
  \forall s_{-i} \in S_{-i} \ \ \ \ \ \ v_i(s_i,s_{-i}) > v_i (s'_i, s_{-i})
  $$
  We notate this with $s_i\succ_i s_i'$. 

* $s_i\in S_i$ is a **strictly dominant strategy** if the following holds
  $$
  \forall s_i' \in S_i \ , s_i\ne s_i' \ \ \ \ \ s_i \succ_i s_i'
  $$
  A strategy profile $s^D\in S$ is a **strictly dominant strategy equilibrium** if $s_i^D\in S_i$ is a strict dominant strategy for all $i\in N$. 
  
* *A rational player never plays a strictly dominated strategy*. Knowledge of the game recognizes dominated strategies and rationality means we avoid them.  

* *Tadelis 4.1*. If the game $\Gamma$ has a strictly dominant strategy equilibrium $s^D$, then $s^D$ is the unique dominant strategy equilibrium. 

* If we stick to the solution concept of strict dominance, we will encounter games for which there will be no equilibrium. *Strict dominance fails to predict player decisions in many games*. 
* *Strict dominance does not imply Pareto optimality*. 

* *Proposition 4.3*. If $s_i$ is a strictly dominated strategy for player $i$, then it cannot be a best response to any $s_{-i}\in S_{-i}$. 
* If strategy $s_i^D$ is a strictly dominant strategy, then it must be a best response to any opponent strategy $s_{-i}$.
# Iterated Elimination
* *Assume*: 
	* All players are rational 
	* A rational player will never play a strictly dominated strategy.
* **Iterated elimination of Strictly Dominated Strategies (IESDS)** lets us rule out strictly dominated strategies that players will never do.
	* Common knowledge implies that players can identify strategies that their rational opponents will never play. And, everyone in the game knows that no one will play a strictly dominated strategy.
	* This process gives us smaller games wherein we can repeatedly apply common knowledge to eliminate strictly dominated strategies until none are left.

* Any strategy profile $s^\text{ES}=\{s_1^\text{ES},\dots,S_2^\text{ES}\}$ that survives the process of IESDS is an **iterated-elimination equilibrium**
	* The iterated-elimination equilibrium *always exists* (even without strict dominance).
	* It is *not unique* when we stop at a payoff matrix consisting of more than one entry. 
	* *Tadelis 4.2*. If for a game $\Gamma$, $s^\ast$ is a strict dominant strategy equilibrium, then $s^\ast$ uniquely survives IESDS. 

## Incorporating Beliefs 
* *Proposition 4.4*. If in a finite normal-form game $s^\ast$ is a strict dominant strategy equilibrium or if it uniquely survives IESDS, then $s_i^\ast$ is a best response to $s_{-i}^\ast$  $\forall i\in N$. 
* A rational player will always play $s_i'$ only when their beliefs about other players' behavior justify the use of $s_i'$.

* We can incorporate IESDS to find the set of **rationalizable strategies** but applied to eliminating strategies that are never a best response. In other words, we ask *what might a rational player do?*. 
# Weak Dominance 
* Let $s_i, s_i' \in S_i$ be possible strategies. $s_i'$ is **weakly dominated** by $s_i$ if, for any possible combination of other players' strategies $s_{-i}\in S_{-i}$ , player $i$'s payoff from $s_i'$ is strictly less than that from $s_i$. That is 

  $$
  \forall s_{-i} \in S_{-i} \ \ \ \ \ \ v_i(s_i,s_{-i}) \ge v_i (s'_i, s_{-i})
  $$
  We notate this with $s_i\succeq_i s_i'$. 

*  $s_i\in S_i$ is a **weakly dominant strategy** if the following holds 
   $$
   \forall s_i' \in S_i \ , s_i\ne s_i' \ \ \ \ \ s_i \succeq_i s_i'
   $$
   
   A strategy profile $s^D\in S$ is a **weakly dominant strategy equilibrium** if $s_i^D\in S_i$ is a weakly dominant strategy for all $i\in N$. 
  
* Unlike strict dominance, *if a weakly dominant strategy equilibrium exists, it need not be unique*

# Nash Equilibrium 

# Links 
* [[Fundamental Constructs in Game Theory]]
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 3 - 6]]
