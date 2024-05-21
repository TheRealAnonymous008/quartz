* **Regret Matching** involves minimizing regret and achieving no-regret outcomes. 
	* **Unconditional Regret Matching** - computes action probabilities proportional to the positive average unconditional regrets of the action. Here, we define **unconditional regret** as follows 
	  
	  $$
	  \text{Regret}_i^z (a_i) = \sum_{e=1}^z \left[ R_i(\braket{a_i,a_{-i}^e}) - R_i(a^e) \right]
	  $$
	  The average unconditional regret is given as
	  $$
	  \bar{R}_i ^z (a_i) = \frac{1}{z} \text{Regret}_i^z (a_i )
	  $$
	  We then perform the update as follows (note that the following still needs to be normalized )
	  
	  $$
	  \pi_i^{z+1}(a_i) \propto \max(0, \bar{R}_i ^z (a_i))
	  $$

* **Conditional regret matching** computes action probabilities proportional to the positive average unconditional regrets of the action. Here, we define **conditional regret** for choosing $a_i'$ instead of $a_i$ as 
	  $$
	  \text{Regret}_i^z (a_i', a_i) = \sum_{e:, a_i^e =a_i'}^z \left[ R_i(\braket{a_i,a_{-i}^e}) - R_i(a^e) \right]
	  $$
	* The average conditional regret is given as 
	  
	  $$
	  \bar{R}_i^z(a_i',a_i) = \frac{1}{z} \text{Regret}_i^z (a_i',a_i)
	  $$
	* The policy is then updated as follows 
	  
	  $$
	  \pi_i^{z+1}(a_i) = 
	  \begin{cases}
	  \frac{1}{\eta} \max(0, \bar{R}_i^z (a_i^z, a_i)) & \text{if } a_i \ne a_i^z \\
	  1-\sum_{a_i'\ne a_i^z} \pi_i^{z+1} (a_i') & \text{otherwise}
	  \end{cases}
	  $$
	  

	* In the formula, we have that 
	  $a_i^z$ is the action chosen in the last episode and 
	  
	  $$
	  \eta > 2 \cdot \max_{a\in A} |R_i(a) | \cdot  (|A_i| - 1) 
	  $$
	  Which is a hyperparameter controlling the bias towards higher conditional regret (higher $\eta$ = lower bias). The lower bound ensures the resulting sum of probabilities $\pi_i^{z+1}(a)\le 1$, when $a_i\ne a_i^z$.   


* The average regret of each agent is bounded by $\kappa \frac{1}{\sqrt{z}}$. *At the limit when $z\to\infty$, regret will approach $0$*. 
* If all agents use conditional / unconditional regret matching, then the empirical distribution of joint actions $\bar{\pi}^z$ will converge to the set of correlated / coarse-correlated equilibria (see [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] for more on this ).
  
  We achieve the following bound under the empirical distribution $\bar{\pi}^z$
  
  $$
  \sum_{a\in A : a_i=a_i'} \bar{\pi}^z (a)  \ R_i (\braket{a_i'', a_{-i}}) \le  \sum_{a\in A : a_i =a_i'} \bar{\pi}^z (a) R_i (a)
  $$
# Links 
* [[MARL from a Game Theoretic Perspective]]

* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] - Ch 6.5