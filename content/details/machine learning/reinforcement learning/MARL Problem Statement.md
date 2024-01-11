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
# Extensions 
* MARL can either be **cooperative** wherein agents work together; **competitive** where the game is zero-sum or a mix of the two. 

* MARL environments can be **homogeneous** in which case all agents share the same set of actions, observations and rewards. 
	* An environment has **weakly homogeneous agents** if for any joint policy $\pi$  and permutation between agents $\sigma: N\to N$, it follows that $\forall i\in N$
	  
	  $$
	  U_i(\pi)= U_{\sigma(i)} \big(\braket{\pi_{\sigma(1), \dots, \pi_{\sigma(N)}}}\big) 
	  $$
	* An environment has **strongly homogeneous agents** if it is weakly homogeneous agents and if the optimal joint policy consists of identical policies, that is 
	  
	  $$
	  \pi^\ast_1= \dots =\pi_N^\ast 
	  $$



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

## Human Interaction 
* [^Zhou_2023] point out various challenges for MARL in the context of different fields. In general these can be grouped as follows: 
	* MARL cannot handle unforeseen circumstances, especially those not seen in training. This can be dangerous (i.e., in an autonomous vehicle context)
	* Considering the human in the loop -- relinquishing control to the human operator as needed or coordinating with them 
	* Providing model interpretability and transparency 
	* Model robustness. MARL can be sensitive to slight perturbations. 
	* In low data settings, MARL heavily relies on sample efficiency. 

* In systems where a MARL system is required to interact with humans, MARL approaches present additional challenges 
	* *Additional Non-stationarity* due to human intervention. 
	* The *diversity* of human behavior with respect to culture,  beliefs, and behavior shifts from interacting with the MARL system. The MARL system needs to model this behavior to integrate with humans better.
	* *Complex Heterogeneity* due to diverse human backgrounds, physical system specifications, and differences between the time scales of the simulation and reality. 
	* *Scalability* especially when the number of agents increases, and considering human factors. 

* As [^Zheng_Trott_2020] points out, AI and human behavior differs substantially, so extending AI to apply to the real world setting requires some form of human "suboptimality"

[^Zheng_Trott_2020]: Zheng et al. (2020) [The AI Economist: Improving Equality and Productivity with AI-Driven Tax Policies](https://arxiv.org/pdf/2004.13332.pdf) . Supplemental [blog](https://blog.salesforceairesearch.com/the-ai-economist/)

## Safety 
* [^Zhou_2023] define the following extension of the regular stochastic game: 
  
  A **safe MARL game** is a stochastic game where each agent has a set of $m^i$ cost functions $\{C_j^i\}_{1\le j \le m^i}^{i\le N}$ where each cost function is of the form $C_j^i:S\times \mathbb{A}\times S\to \mathbb{R}$  with cost constraining values $c^i$.  
  
  The goal of the agents is to still maximize reward subject to the constraint that 
  
  $$
  J_j^i(\pi) = \mathbb{E}_\pi \bigg[\sum_{t=0}^\infty \gamma^t C_j^i (s_t,a_t, s_{t+1} \mid s_0=s)\bigg] \le c_j^i
  $$

* Meeting the safety requirements should not lead to a degradation in model performance. 

* A **state-adversarial stochastic game** is a stochastic game with an additional set $\mathcal{B}^j$ called the uncertainty set of adversarial states of agent $j$.
  
  Given a joint policy $\pi$ and the joint adversarial perturbation $v:S\to \mathcal{B}^1\times\dots\times \mathcal{B}^M$ where $M\le N$ agents are attacked, we have the following [[Backups in Reinforcement Learning|Bellman equation]]
  
  $$
  \hat{V}_\ast ^i (s) = \max_{\pi^i(\cdot\mid s)} \min _{v}  \sum_{a\in \mathbb{A}} \pi(a\mid s,v(s))\sum_{s^i\in S} \bigg(\mathcal{T}(s'\mid s,a)\big(R^i(s,a,s') + \gamma \hat{V}_\ast^i (s') \big) \bigg)
  $$

Here *robustness comes from mitigating against perturbations in observed states*

* A **model-adversarial stochastic game**  is a stochastic game where we have uncertainty sets for the reward functions and transition probabilities $\hat{\mathcal{R}}^i$ and $\hat{T}$. 
  
The Bellman equation is given as 

   $$
  \hat{V}_\ast ^i (s) = \max_{\pi^i(\cdot\mid s)} \min _{\hat{R}_i\in\hat{\mathcal{R}}_i : \hat{\mathcal{T}}\in\hat{T}} \sum_{a\in \mathbb{A}} \pi(a\mid s,v(s))\sum_{s^i\in S} \bigg(\mathcal{T}(s'\mid s,a)\big(R^i(s,a,s') + \gamma \hat{V}_\ast^i (s') \big) \bigg)
  $$

Here *robustness comes from mitigating against perturbations in the environment's model -- transition functions and rewards*


* **Data Poisoning** - is an attack where attackers modify the rewards in a dataset to encourage each agent to adopt a harmful target policy with minimal modifications. Applies for offline MARL  
* **Adversarial Attacks** - involves manipulating agent observations to reduce the overall team reward in a cooperative setting. 
* **Backdoor Attack** - it conspires to manipulate both the actions and the rewards of the poisoned agents. It uses three modules -- trigger design, action poisoning, and reward hacking. 

* Robustness comes from improving the following aspects of training 
	* State observations 
	* Actions - considering how the actions of agents interact with each other. 
	* Rewards and Models - estimate the uncertainty set of a model adversarial stochastic game.  
	* Adversarial Policies - detect Trojan agents and their triggers. It also includes methods to un-learn detected backdoors. 
	* Communication

[^Zhou_2023]: Zhou, Liu, and Tang (2023) [Multi-Agent Reinforcement Learning: Methods, Applications, Visionary Prospects, and Challenges](https://arxiv.org/pdf/2305.10091.pdf)
# Links 
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] 
	* Ch. 9.7 talks about homogeneous agents

* [[MARL from a Game Theoretic Perspective]]