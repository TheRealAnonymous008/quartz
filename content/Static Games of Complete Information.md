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
* A **Nash Equilibrium** is a system of beliefs and a profile of actions for which 
	* Each player is playing a best response to his beliefs 
	* Players have correct beliefs. 
  
  More formally. A pure strategy profile $s^\ast = (s_1^\ast, s_2^\ast, \dots, s_n^\ast)\in S$ is a Nash Equilibrium if $s_i^\ast$ is a best response to $s_{-i}^\ast$ for all $i\in N$. That is
  
  $$
  v_i(s_i^\ast, s_{-i}^\ast) \ge v_i (s'_i ,s^\ast_{-i}) \ \ \ \ \ \forall s_i'\in S_i \ \wedge \ i \in N 
  $$

* *Tadelis 5.1*. Let $s^\ast$ be a strategy profile. If $s^\ast$ is either 
  
  (1) a strict dominant strategy equilibrium 
  (2) the unique survivor of IESDS
  (3) the unique rationalizable strategy profile 
  
  Then $s^\ast$ is the unique  Nash Equilibrium. 

* *The constraint that players have correct beliefs is demanding* It requires that players predict the behavior of their opponents. Such beliefs may even be based on past experience. 

* Procedure for finding Nash Equilibria:
	* For every strategy of player $-i$, find the highest payoff entry for players $i$ for all possible strategies. 
	* Any entry where all payoff entries have been marked for all players is a Nash Equilibrium. This is when all players are playing a best response. 

* *Nash Equilibrium does not guarantee Pareto optimality*.

### Conditions for Nash Equilibrium 
* Under certain conditions, the Nash Equilibrium will exist. For most games, these conditions will hold. 

# Example Games 
* The **Stag Hunt Game** involves two players. They can choose to either hunt a stag or a hare. The stag gives a better bounty, but it requires both players. Hunting a hare can be done with one player but is less filling. The payoff matrix is given as 
  
  $$
  \begin{bmatrix}
  & \text{S} & \text{H} \\
  \text{S} & a,a & c,b \\ 
  \text{H} & b,c & d,d
  \end{bmatrix}
  $$
  Where $a>b\ge d > c$. 
  
  
* The **Cournot Duopoly** involves the following specifications. Here, we have two firms that can set the number of product they would produce.  
	* $N=\{1,2\}$. The players represent firms
	* $S_i=[0,\infty]$ so that each firm sets a positive quantity. $s_i\in S_i$. 
	* The payoff is given by the following. Assume $i\ne j$ 
	  
	  $$
	  v_i(s_i,s_j) = 
	  \begin{cases}
	  (100 - s_i-s_j) - s_j^2 & \text{if } s_i+s_j< 100 \\ 
	  -s_i^2 & \text{if } s_i +s_j \ge 100
	  \end{cases}
	  $$
	  
	  * The best response function of each player is downward sloping. More produce = Lower best response quality of opponent. 
	    
* The **Bertrand Duopoly** involves the following specifications. Here we have two firms that set the price they produce. 
	* $N={1,2}$. The players are referred to as firms. 
	* $S_i=[0,\infty]$ so that each firm sets a positive price $p_i\in S_i$
	* Let $q_i$ be the quantity produced by $i$ 
	* Demand is given as $p = 100 - q$ and the cost is given as $c_i(q_i)=10q_i$. 
	* The payoffs are given using the following
	  
	  $$
	  v_i(p_i,p_j) = 
	  \begin{cases}
	  100 - p_i & \text{if } p_i < p_j  \\ 
	  0 & \text{if } p_i > p_j \\ 
	  \frac{100-p_i}{2} & \text{if } p_i=p_j
	  \end{cases}
	  $$

	* *Tadelis 5.2*. For $\epsilon = 0$ and where firms can set their price to  be any real number, there is a unique Bertrand-Nash equilibrium obtained by $p_1=p_2=c$
	* For prices between marginal costs and the monopoly price, the higher the best response price of player $i$, the higher the price set by player $j$.

* **Hotelling's Model** involves political candidates positioning themselves in the political spectrum. 
	* Say that we have an interval $[-50, 50]$ representing the political spectrum ($-50$ is the most left-leaning, $50$ the most right-leaning).  
	* Each candidate $i$ chooses a platform as a policy $a_i \in [-50,50]$. Citizens choose candidates that platform close to their preferences.  The outcome is determined by majority rule. 
	* *Assume*: There are an odd number of citizens so a tie is impossible unless someone is indifferent. When someone is indifferent they choose randomly. 
	* *Assume*: Winning is preferable to a tie. A tie is preferable to losing. 
	* The best response is given as 
	  
	  $$
	  \text{BR}_i (a_j) = 
	  \begin{cases}
	  [a_j + 1, -a_j-1] & \text{if } a_j < 0 \\
	  0 & \text{if } a_j = 0 \\ 
	  [-a_j + 1, a_j-1] & \text{if } a_j > 0
	  \end{cases}
	  $$
	* The Nash Equilibrium is $0,0$ i.e., both candidates favor being centrists.
	* The **Median Vector Theorem** states that if voters are different from one another along a single dimensional “preference” line, as in Hotelling’s model, and if each prefers his own political location, with other platforms being less and less attractive the farther away they fall to either side of that location, *the political platform located at the median voter will defeat any other platform in simple majority vote.* 
		* The median is defined as that which splits the spectrum into two equal halves (generalizable even for the continuous formulation of the problem)
# Links 
* [[Fundamental Constructs in Game Theory]]
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 3 - 6]]
