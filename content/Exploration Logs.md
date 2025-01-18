* [Introversion Games - Subversion](https://www.youtube.com/watch?v=1giu6sMnAxY)

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

* [^Vanneste_2021] examines communication learning in a mixed cooperative-competitive, partially-observable multi-agent setting where goals are shared between teams and are competitive across teams. 
	* Communication is done via a C-Net which takes in observations and outputs a vector message..
	* An A-Net then uses the vector message and the observations in the environment to determine the next action.
	* Communication is learnt via Differentiable Inter-Agent Learning
	* *Limitation*: In scenarios where communication is shared across teams, performance will decline significantly
	* *Limitation*: Not tested for cases with a large number of agents.
[^Vanneste_2021]: Vaneste et al. (2021) [Mixed Cooperative-Competitive Communication Using Multi-Agent Reinforcement Learning](https://arxiv.org/abs/2110.15762) 


* [^Bahceci_2023] examines how strategies can be evolved for use in Competitive Multi-Agent Search (CMAS). It gives a framework for viewing human creative problem solving as CMAS. 


[^Bahceci_2023]:: Bahceci, Katila, and Mikkulainen (2023) [Evolving Strategies for Competitive Multi-Agent Search](https://arxiv.org/abs/2306.10640)


* Some approaches in RL for learning strategy:
	* [[Transfer Learning]]
	* [[Imitation Learning]]
	* Competitive Learning - learn how to counter an opponent's actions in a simple game. 
	* Continual Learning - the model constantly adapts. 

# Topic Queue
* [Screaming Insects Algorithm](https://www.youtube.com/watch?v=Yu7sF9rcVJY)
* [Look more into Sparse Autoencoder](https://www.youtube.com/watch?v=9-Jl0dxWQs8)
* [Proportional Navigation](https://en.wikipedia.org/wiki/Proportional_navigation)

# File
* [Demo and Writeup for the AI of a Tactical Top Down Shooter](https://www.gamedev.net/blogs/entry/2267533-close-quarters-development-realistic-combat-ai-part-i/)
* [Final Fantasy VII - Game AI Writeup](https://gamefaqs.gamespot.com/ps/197341-final-fantasy-vii/faqs/31903)
* [Predictive Aiming](https://yal.cc/simplest-possible-predictive-aiming/)



# Paper Queue
* [^lyu_2023] provides a theoretical and empirical analysis of the use of Centralized Critics in CTDE.

[^Lyu_2023]: Lyu et al. (2023) [On Centralized Critics in Multi-Agent Reinforcement Learning](https://dl.acm.org/doi/pdf/10.1613/jair.1.14386) 

* [^Kim_2023]   introduces a new mutual information framework for MARL. This leads to the development of an algorithm called **Variational Maximum Mutual Information, Multi-Agent Actor Critic** which allows agents to coordinate simultaneous actions without latency. 

[^Kim_2023]: Kim, Jung, Cho, Sung (2020) [A Maximum Mutual Information Framework for Multi-Agent Reinforcement Learning](https://arxiv.org/pdf/2006.02732)

* Branching Reinforcement Learning by Du, and Chen (Jun 15, 2022) 
* Vinyals et al. (2019) [Grandmaster level in StarCraft II using multi-agent reinforcement learning](https://www.seas.upenn.edu/~cis520/papers/RL_for_starcraft.pdf) 
	* Linked in [[Self Play]]
* Wu et al. (2017) [Scalable trust-region method for deep reinforcement learning using Kronecker-factored approximation](https://arxiv.org/pdf/1708.05144.pdf)
	* Linked in [[Trust Region Policies]]
* [Ecoclimates -- Climate-Response Modeling of Vegetation by Palubicki et al. (2022)](https://storage.googleapis.com/pirk.io/papers/Palubicki.etal-2022-Ecoclimates.pdf)
* Ma et al. (2024) [Foundation Methods for Music -- A survey](https://arxiv.org/pdf/2408.14340v2)

# Front Logs
* [[Numerical Methods]] 
	* ODEs
	* PDEs
* [[Fuzzy Computation]] and Fuzzy Logic
* Algebraic Graph Theory

# Backlogs
* Note, some entries in [[Trivia]] are also interesting.

* Forms of Government

* [[Theory of Computation]]
* [[Rigid Body Simulation]] - Nonpenetration constraints
* Japanese Mythology
* [[Graph Neural Network]] - GNNs
* Combinatorial Optimization
* Ballistics
* [[Graph Theoretic Approaches for Swarms]] - Resume Ch. 4
* [[Code Complete by McConnell]] - Resume Ch. 10
* [[Philosophy]] - read through [[A New History of Western Philosophy  By Anthony Kenny]] 

* [[Factory Physics]] - Workforce Planning.
* [[Virtues and their Vices by Kevin and Craig]]  -Cardinal Virtues, Intellectual Virtues, Theological Virtues
* [[Linear and Nonlinear Programming by Luenberger and Ye]] - Resume Ch. 5
* [[Drawing on the Right Side of the Brain by Edwards]] - Resume Ch. 8
* [[Ordinary Differential Equations by Arnold]] - Ch. 6 (but restart all of Part 1) with better math background

* [HEMA](https://wiktenauer.com/wiki/Main_Page)
* Extreme Performance Artists. Prompted by [this](https://www.youtube.com/watch?v=GrBZuCQAPAw) 
* [Dramaturgy](https://en.wikipedia.org/wiki/Dramaturgy_(sociology))
* [Von Neumann Morgenstern Utility Theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem)
* [Petri Nets](https://en.wikipedia.org/wiki/Petri_net#:~:text=A%20Petri%20net%2C%20also%20known,of%20elements%3A%20places%20and%20transitions.)
* [Hopfield Networks](https://www.youtube.com/watch?v=1WPJdAW-sFo&list=WL&index=15)
* General Method of Moments / Simulated Method of Moments
* [AlphaFold](https://en.wikipedia.org/wiki/AlphaFold)
* [Socionics](https://en.wikipedia.org/wiki/Socionics)
* Chess Openings
* [Sound Design](https://www.youtube.com/watch?v=_J56n496u6k)
* [Johnson-Lindenstrauss Lemma](https://en.wikipedia.org/wiki/Johnson–Lindenstrauss_lemma)
* [Dreams are (theorized) as ways humans prevent overfitting](https://www.sciencedirect.com/science/article/pii/S2666389921000945)
* Neuro Evolution of Augmented Topologies and similar algorithms
* Compositional Pattern Producing Methods
* Lanczos Algorithm (cited in [[Graph Neural Network#Lanczos Network|Lanczos Networks]])
* Algorithmic Information Theory
* [Some interesting things to explore further](https://www.youtube.com/watch?v=-uIwboK4nwE) - PSLQ, Sinkhorn Limits, Kruithoff Limits
	* https://en.wikipedia.org/wiki/Iterative_proportional_fitting 
* [Combinatorial Maps](https://en.wikipedia.org/wiki/Combinatorial_map)
* [Surface Nets](https://bonsairobo.medium.com/smooth-voxel-mapping-a-technical-deep-dive-on-real-time-surface-nets-and-texturing-ef06d0f8ca14)
* [Halton Sequences](https://en.wikipedia.org/wiki/Halton_sequence)
