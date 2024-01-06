# Convergence and Learning Performance 
* For the following, let $\pi^z$ be a joint policy and the solution be $\pi^\ast$
* *Note*: Convergence is hard to check in practice. 

* *Infinite Data*
  $$
  \lim_{z\to \infty} \pi ^z= \pi ^\ast 
  $$
* *Expected Return*
  $$
  \lim_{z\to \infty} U_i (\pi^z) = U_i (\pi^\ast), \ \forall i \in N
  $$
* *[[Model Performance|Empirical Distribution]]*
  $$
  \begin{split}
  \lim_{z\to \infty} \bar{\pi}^z &= \pi^\ast \\ 
  \bar{\pi}^z &= \frac{1}{z}\sum _{e=1}^z \pi^e(a\mid h)
  \end{split}
  $$
* *Averaged Joint Policy*. This is equivalent to the empirical distribution equivalence except we use the following 
$$
\bar{\pi}^z = \frac{1}{|H^z (h)|}\sum _{(a^\tau, h^\tau) \in H^z(h)} [a=a^T]_1
$$
Where $(a^\tau, h^\tau)_{\tau=0}^t$ is the sequence of joint actions sampled from the joint policy conditioned on the history $h^\tau$. 

* Convergence of empirical distribution to a *set of solutions* 
  
  Let $d$ be some distance metric (such as those used in a [[Loss Function]]) 
  
  $$
  \forall \epsilon >0 \ \exists z_0  \  : \forall z > z_0 \ \exists \pi ^\ast : d(\bar{\pi}^z , \pi^\ast ) < \epsilon 
  $$

* *Average return* 
$$
\lim_{z\to \infty} \ \bar{U}_i^z = U_i(\pi ^\ast ) \ \forall i \in N
$$
Where $\bar{U}_i^z$ denotes the average return across episodes.   
# Challenges 
* Most algorithm for single-agent RL cannot be extended as *MARL has intrinsic non-stationarity due to the environment changing with agent actions, and the agents themselves changing.* 
	* This becomes more of a problem when using [[Function Approximation in Reinforcement Learning|Function approximation]] or [[Policy Gradient Methods|PGMs]]. 

* The environment needs to be accurately modeled.
* Agent goals may be significantly different to each others. Policy sharing becomes more difficult. 

* When the environment has multiple equilibria, **equilibrium selection** is needed -- we need to establish which equilibrium should the agents agree on and why? 
	* One approach to this is to further constrain the solution space with additional criterion such as Pareto optimality. 
	* Another is to exploit the structure of the game. 
	* **Agent modeling** can also be used where agents predict the actions of other agents and act accordingly (in a similar manner [[Dynamic Games of Complete Information|here]])
	* Communication can also be used but this requires more consideration as the problem becomes more complex. 

* **Multi-Agent Credit Assignment** - in MARL, there is the question of *whose actions among the agents contributed to the rewards*. 
	* This requires that agents understand the causal relation between their actions and rewards and that of the other agents' actions. 
	* One approach is to assign values to joint actions. 
	* **Difference Rewards** - an approach where the agent considers what reward they would have received if the other agents chose a different action than what they actually chose. 
	* We may also learn decompositions of the collective reward. 

* Scalability. More agents means more work needed
	* More agents = Larger joint action space and potentially larger state space. 
	* More agents also means more non-stationarity in the environment. 

* It is hard to define optimality for a MARL environment. 

* MARL can either be **cooperative** wherein agents work together; **competitive** where the game is zero-sum or a mix of the two. 
# Links 
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer]] 
* [[MARL from a Game Theoretic Perspective]]