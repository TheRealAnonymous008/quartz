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
# Links 
* [[Fundamental Constructs in Game Theory]]
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 3 - 6]]
