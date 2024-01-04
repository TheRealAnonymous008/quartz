* **Joint Action Learning** uses [[Temporal Difference Learning]] to learn estimates of the joint-action value models to estimate the expected returns 
* Here we use something similar to $Q$-learning but for joint action $a$
  
  $$
  Q_i ^\pi (s,a ) = \sum_{s'\in S} \ \mathcal{T}(s'\mid s,a) \bigg[  R_i(s,a,s') +\gamma \sum_{a'\in A} \pi(a'\mid s') \ Q_i^\pi (s',a') \bigg]
  $$
  
* **JAL-GT** is a variant of this where we frame the problem as a [[Static Games of Incomplete Information|Static game]] $\Gamma_{s}(a)$ with the reward function being given as. 
  $$
  \Gamma_{s,i}(a) = R_i(a_1,\dots,a_n) = Q_i(s,a_1,\dots, a_n) 
  $$
	* *Learning $Q$ then becomes discovering the right game to play*

![[JAL.png]]
<figcaption>  JAL-GT. Image taken from Albrecht, Christianos and Schafer </figcaption>

* We solve $\Gamma_s$ using a game theoretic solution concept to obtain the solution -- a policy $\pi^\ast_s$ from which $a\sim \pi^\ast_s$ 
	* **Minimax Q-Learning** is guaranteed to learn the unique minimax value of the stochastic game under the assumption of [[Monte Carlo Methods in Reinforcement Learning|all joint actions and states being tried infinitely often]].  
		* Policies trained under Minimax Q-Learning do not necessarily exploit weaknesses to opponents when they exist. 
		* At the same time, Minimax policies are *robust to exploitation by assuming a worst-case opponent during training*
	* **Nash Q-Learning** is guaranteed to learn a Nash equilibrium and is applicable to general-sum games but *it is very restrictive*
		* It requires that all joint actions and states being tried infinitely often, and all normal-form games either 
			* Have a global optimum where each agent individually achieves its maximum possible return ; or 
			* Have a saddle point in which if any agent deviates, then all other agents will receive a higher expected return. 
		* These assumptions bypass the equilibrium selection problem since in either a global optimum or a saddle point, the expected return of each agent is the same. 
		* *Implicitly, we have that agents consistently choose either global optima or saddle points*. 
	* **Correlated Q-Learning** uses a correlated equilibrium but we need to modify the algorithm so that agents sample from correlated equilibrium $\pi$ instead
		* This has an advantage over Nash Q-Learning 
			* It explores more solutions with potentially higher expected returns 
			* It can be computed efficiently with [[Linear Programming]]
		* Convergence to a correlated equilibrium is not guaranteed.
		* Equilibrium selection becomes a concern, however this can be mitigated using a protocol to consistently select an equilibrium (i.e., highest welfare) 

### Limitations 
* JAL is not applicable to certain games since information in the joint action value model $Q_i(s,a)$ is insufficient to construct an equilibrium policy. *The limitations come in finding a deterministic equilibrium but for a game where many stochastic equilibria exist instead*.

* A **stationary equilibrium** is one which is not conditioned on the state $s$ rather than the history $h$. s
* **No Stationary Deterministic Equilibrium Theorem** (*Zinkevich, Greenwald, and Litman (2005)* ) 
  
Let $Q_i^{\pi,\Gamma}/V_i^{\pi,\Gamma}$ denote the $Q_i^\pi/V_i^\pi$ functions in game $\Gamma$. For any NoSDE game $\Gamma$ with a unique equilibrium joint policy $\pi$, there exists another NoSDE game $\Gamma'$ which differs from $\Gamma$ only in the reward functions and has its own unique equilibrium joint policy $\pi'\ne\pi$ such taht 

$$
\forall i : Q_i^{\pi,\Gamma} =Q_i ^{\pi', \Gamma'} \ \ \ \ \  \exists i :V_i^{\pi,\Gamma}\ne V_i^{\pi',\Gamma'} 
$$ 
* Specific action probabilities may not be computable using $Q$ functions alone

# Links 
* [[MARL Problem Statement]]
* [[MARL from a Game Theoretic Perspective]]

* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] - Ch 6.2