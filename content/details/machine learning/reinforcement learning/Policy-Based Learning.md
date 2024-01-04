* MARL extension of [[Policy Gradient Method Algorithms|PGM algorithms]]. They *gradually vary the action probabilities within a learned policy*.

## IGA
* We can perform [[Optimization Algorithm#Gradient Descent|Gradient Descent]] to update the policy *towards maximizing the expected reward.*
* A variant is called  **infinitesimal gradient ascent (IGA)** defined for two agents and two actions. 
* *Assumption*: Agents have knowledge of their reward matrix 
* In IGA, we update the gradient in an unconstrained manner and then project it so that it becomes a valid probability distribution. 

* IGA is not guaranteed to converge with a fixed learning rate. It will converge when we vary the learning rate and the overall step size is bounded. We follow the **win or learn fast**. 
	* If the agent is losing, it should try to adapt quickly (i.e., high learning rate)
	* If the agent is winning it should adapt slowly since the other agent will adapt (i.e., low learning rate) 
	* Winning is determined by comparing the actual expected reward with the expected reward achieved by a Nash equilibrium policy. 
	* Mixed with IGA we call this **WoLF-IGA** and it is guaranteed to converge to a Nash Equilibrium in general-sum games with two agents and two actions.

## WoLF-PHC
* **WoLF-IGA** is generalized to **WoLF with Policy Hill Climbing** which is applicable for a general sum game with any number of agents and actions. It also removes the requirement of knowledge about the reward function or policy 
	* It learns $Q$ as in standard [[Temporal Difference Learning#Q-Learning|Q learning]] 
	* It makes use of an average policy $\bar{\pi}_i$ computed over past policies. *Rationale*: As in [[Agent Modeling#Fictitious Play|Fictitious play]], the average policy will converge to a Nash equilibrium (in most cases).
	* $l_l, l_w \in [0,1]$ are the learning rates for losing and winning.

![[WoLF-PHC.png]]
<figcaption> WoLF-PHC. Image taken from Albrecht, Christianos and Schafer </figcaption>

* In the above, $\Delta(s,a_i)$ determines how to move the policy $\pi_i$ closer to the greedy policy with respect to $Q$, calculated as  *moving probability mass* $\delta_{s,a_i}$ from all non-greedy actions to the greedy actions.  We have the following 
  
  $$
  \begin{split}
  \Delta(s,a_i) &=
  \begin{cases}
  -\delta_{s,a_i } & \text{if } a_i \notin \underset{a_i'}{\text{argmax}}  \ Q(s,a_i') \ \text{ (i.e., not a greedy action)} \\ 
  \sum_{a_i'\ne a_i} \delta_{s,a_i'} & \text{otherwise for greedy actions}
  \end{cases} \\
  \delta_{s,a_i} &= \min \bigg( \pi_i(a_i\mid s), \frac{\delta}{|A_i|-1}\bigg) \\ 
  \delta &= 
  \begin{cases}
  l_w & \text{if } \sum_{a_i'} \pi_i (a_i'\mid s) \ Q(s,a_i') > \sum_{a_i'} \bar{\pi}_i(a_i'\mid s) \ Q(s,a_i')  \ \text{ (i.e., winning)} \\ 
  l_i & \text{otherwise }
  \end{cases} 
  \end{split}
  $$

* The minimum in the definition of $\delta_{s,a_i}$ ensures no more of the mass than what was allocated is moved. 
* *It improves upon fictitious learning by making the policy updates smoother* [^wolf_phc_1]
[^wolf_phc_1]: This is similar to [[Trust Region Policies#PPO|PPO]] for regular PGMs. 

## GIGA
* **Generalized Infinitesimal Gradient Ascent (GIGA)** generalizes IGA to normal-form games with more than two agents and actions such that we achieve [[MARL Problem Statement|no-regret]]. 
* *Assumption*: The past actions of other agents can be observed. 

* Like [[#IGA]], we update using the unconstrained gradient, however *we use the gradient in terms of the actual rewards after observing the past actions of other agents*. 
* The expected reward for an agent $i$ against the actions of the other agents is given as 
  
  $$
  U_i (\pi_i,a_j) = \sum_{a_i\in A_i} \pi_i(a_i) R_i (a_i,a_{-i})
  $$
  The update rule then becomes the following, using step size $\kappa^k$ and projection operator $P(x)$ that projects the vector $x$ to the [[Game Theory - Strategy|simplex]] $\Delta(A_i)$. *Note* that $k$ is a superscript for the episode 
  
  $$
  \begin{split}
  \hat{\pi}^{k+1} &\gets \pi_i^k + \kappa^k  \ \nabla_{\pi^k_i} \  U_i (\pi_i^k, a_{-i}^k) \\
  P(x) &= \underset{x'\in \Delta (A_i)}{\text{argmin}}  \ ||x-x'|| \\ 
  \pi_i^{k+1} &\gets P(\hat{\pi_i}^{k+1})
  \end{split}
  $$
  

* GIGA achieves no-regret if all agents use a step size of $\kappa^k = \frac{1}{\sqrt{k}}$. In particular the regret is bounded by 
  
  $$
  \text{Regret}_i^k \le \sqrt{k} + \bigg(\sqrt{k} + \frac{1}{2}\bigg)|A_i| r^2 _\text{max}
  $$
  Where $r_\text{max}$ is the maximum reward the agent can receive. 
	* This implies that the empirical action distribution of agents using GIGA converges to coarse-correlated equilibrium 

# Links 
* [[MARL from a Game Theoretic Perspective]]

* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] - Ch 6.4 
	* 6.4.5 - Contains a discussion of GIGA for the case of two player games. 