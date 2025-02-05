
* [^Mahlau_2024] proposes **ALBATROSS** (AlphaZero for Learning Bounded-rational Agents and Temperature-based Response Optimization using Simulated Self-Play) for learning both cooperation and competition in simultaneous games. 
	* It makes use of opponent modeling where we use a continuous temperature parameter $\tau$ to estimate opponent skill.   The opponent model makes use of the **Smooth Best Response Logit Equilibrium**. 
		* The **Smooth Best Response** is a softmax over the original utilities $u_i$. That is
		  $$
		  \text{SBR}(\pi_{-i},\tau) \propto\exp(\tau u_i (\cdot,\pi_{-i}))
		  $$
		* A joint policy is called a **Logit Equilibrium** if all agents play the SBR.
		* The SBRLE is the joint policy of the Logit Equilibria of weak agents and the rational agent's response to the Logit Equilibria. 
		  
		  That is, $\forall j\in -i$, $\pi_j$ is a Logit Equilibrium policy with temperature $\tau_j$. 

	* Albatross is derived from [[Decision Time Planning|AlphaZero]] but fine tuned using [[Self Play]] and planning.  It learns to approximate the SBRLE
		* Albatross cooperates with rational partners, is robust to weak allies, and can exploit weak adversaries.
		* A **proxy model** predicts $v_{\theta_P}(o_i\mid \tau)$ and $\pi_{\theta_P}(o_i\mid \tau)$
		  
		  The value function approximates the Logit Equilibrium given $\tau$ and the policy $\pi_{\theta_P}$. 
		* A **response model** works as follows: For agent $i$, define the temperature vector of all other agents as $\tau_{-i}$. The response model predicts $v_{\theta_R}(o_i\mid \tau_{-i})$ and $\pi_{\theta_R}(o_i\mid \tau_{-i})$.
		  
		  The value function is used to approximate a SBR with fixed response temperature $\tau_R$ to the action utilities. 
	* In inference time, the temperature is estimated using Maximum Likelihood Estimation. Let $i$ be the rational agent approximating the temperature $\tau_j$, $j\in -i$.  Given $K$ observations of actions and policies for these agents, we have the log likelihood $l(\tau_j)$ of $j$ exhibiting temperature $\tau_j$ as 
	  $$
	  \begin{split}
	  l(\tau_j) &= \sum_{k=1}^K \left[\tau_j u_j^k (a_j^k,\pi_{-j}^k ) -\ln\sum_{a_j\in A_j} \exp\left(\tau_ju_j^k (a_j,\pi_{-j}^k )\right)\right] \\
	  
	  \frac{\partial l}{\partial\tau_j} &= \sum_{k=1}^K\left[u_j^k (a_j^k,\pi_{-j}^k) - \frac{\sum_{a_j\in A_j}u_j^k (a_j,\pi_{-j}^k) \exp\left(\tau_ju_j^k(a_j,\pi_{-j}^k)\right)}{\sum_{a_j\in A_j}\exp\left(\tau_ju_j^k \left(a_j,\pi_{-j}^k\right)\right)}\right]
	  
	  \end{split}
	  $$
	  Optimal play is determined by using the policy of the proxy model with the highest temperature with the maximum likelihood. 

	* *Limitation*: The estimation converges within $20-30$ timesteps. Shorter games may not benefit from Albatross.
	* *Limitation*: Planning is dependent on the joint action space. 
[^Mahlau_2024]: Mahlau, Schubert, and Rosenhahn (2024) [Mastering Zero-Shot Interactions in Cooperative and Competitive Simultaneous Games](https://arxiv.org/abs/2402.03136)


* [^Barros_2023]  proposes **WINNE**,  a [[Contrastive Learning|contrastive learning]] model for MARL that learns representations for competitive games, as well as model how adversaries might play. 
	* The model learns how to represent patterns on a game strategy of individual opponents and derives a strategy to play against these strategies.  
	* The framework is reliant on three requirements
		* *The model knows how to play the game.*  This is done using a **global policy network** that *learns a general strategy for the game*
		* *The model knows how the opponent plays the game*. This is done using a **Contrastive Strategy Prediction network** that *predicts the opponents actions.*
		* *The model knows how to mitigate any opponent's actions* This is done using a **local policy neural network** that maps the representation learned by the CSP with a set of best possible actions coming from the global network. 
	* The balance between generalized and personalized strategy allows WINNE to escape from the catastrophic forgetting problem. 
	* At the same time, the framework can adapt to its opponent's strategies 
	* If the opponent has no strategy, then the model cannot adapt since the CSP model cannot learn.

![[WINNE Model.png]]
<figcaption> WINNE model. Image taken from Barros and Sciutti, 2023 </figcaption>

[^Barros_2023]: Barros and Sciutti (2023) [All by Myself: Learning Individualized Competitive Behaviour with a Contrastive Reinforcement Learning optimization](https://arxiv.org/abs/2310.00964)

# Links
* [[MARL Deep Learning]]
* [[MARL Algorithms and Approaches]]