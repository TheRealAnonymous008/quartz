# Problem Statements
* [^Yang_2021] We formulate the MARL problem using an extension of [[Markov Processes in Machine Learning|MDPs]]. 

[^Yang_2021]: Yang and Wang (2021). [An Overview of Multi-agent Reinforcement Learning from Game Theoretical Perspective](https://arxiv.org/pdf/2011.00583.pdf)

* A **stochastic [[Game Theory|game]]** is defined as a set of key elements
  
  $N$ is the number of agents. 
  $S$ is the set of environmental states shared by all agents. $\bar{S}\subset S$ denotes terminal states of the environment
  $A_i$ is the set of actions of the $i$-th agent. The set of all action configurations is denoted $\mathbb{A}=\mathcal{A}^1\times\dots\times \mathcal{A}^N$ 
  $R_i: S\times \mathbb{A} \to S$ is the reward function for the $i$-th agent
  $\mathcal{T}:S\times\mathbb{A}\times S\to [0,1]$ for each time step $t\in N$ gives the **transition probability** from state $s$ to $s'$ given action $a$ was taken. 
  $\mu: S\to [0,1]$ gives the **initial state distribution**.  We sample the initial state from this. 
  
  As a convention, we use the superscript $a^i$ for the $i$-th agent and $a^{-i}$ for all other agents. 

* In this context, *all agents simultaneously make decisions (we have a static game)*. Each agent aims to find a policy $\pi^i$ so that its reward function is maximized. The environment, in turn, can *change in response to the agents' actions*. 
* The **joint action** $a^t$ pertains to an element of $\mathbb{A}$. That is, it is of the form $(a_1^t, \dots, a_n^t)$.
* The policy of the agent is conditioned on its history [^1], that is $\pi_i(a_i^t\mid h^t)$.  The history contains the states and the joint actions.
* Like [[Markov Processes in Machine Learning|MDPs]], we assume the Markov property for $\mathcal{T}$.

[^1]: Information sets in [[Dynamic Games of Complete Information|Game Theory]] terms. 

* A more general form introduces the notion of **partial observability**. A **partially observable stochastic game (POSG / POMDP)** is one where the agent can only receive [[Dynamic Games of Incomplete Information|incomplete information]] about the environment.  More formally, it adds for each agent in a stochastic game 
  
  $O_i$ - a finite set of observations 
  $\mathcal{O}_i: A\times S\times O_i \to [0,1]$  - defines the **observation function** that specifies probabilities over the agent's possible observations. It is written as $\mathcal{O_i}(o_i^t\mid a^{t-1}, s^t)$. 

	* The probability of a joint observation is calculated as 
	  
	  $$
	  \mathcal{O}(o^t\mid a^{t-1}, s^t) = \prod_{i\in N} \mathcal{O}_i(o_i^t\mid a^{t-1}, s^t)
	  $$

	* A special case where all agents have the same reward function is called a **Decentralized POMDP (Dec-POMDP)**
	* Observability conditions introduce special cases  such as 
		* The agents do not observe the actions of the other agents. $o_i^t =(s^t,a^{t-1})$ 
		* The agents may observe only a subset of the state and joint action due to having a limited view of the environment $o_i^t=(\bar{s}^t, \bar{a}^t)$, where $\bar{s}^t\subset s^t$ and $\bar{a}^t\subset a^t$. 
		* A noisy environment. This happens when multiple possible observations occur with non-zero probability. 

	* This necessitates the use of beliefs through a **belief state** $b_i^t$ that encodes the probability of the states the environment may be in at time $t$. It follows [[Bayesian Statistics|Bayes rule]] to form a posterior distribution updated through **belief state filtering**
	  
	  $$
	  b_i^{t+1} (s') \propto \sum_{s\in S} b_i^t(s) \ \mathcal{T}(s'\mid s,a_i^t ) \ \mathcal{O}_i (o_i^{t+1}\mid a_i^t, s')
	  $$
		* Note that updating the belief states is a complex task especially for multiagent environments. 
		* *This is mitigated by assuming that agents do not have exact knowledge of the elements of a POMDP*. They can be approximated through [[Recurrent Neural Network|RNNs]]


* The **full history** up to time $t$ is denoted as $\hat{h}^t$. It is of the form $(s^0, o^0, a^0, \dots, s^t, a^t)$

* We may introduce *communication as an action* that is observed by the agents but does not affect the environment. In such a case, we have an action space $A_i$ that is a combination oof an environment action space $X_i$ and a communication action space  $M_i$
  
  $$
  A_i = X_i \times M_i
  $$
  
  The actions in $M_i$ do not affect the environments. $\mathcal{T}$ is independent of $M$.
	* A standard *assumption*: Agents do not know the meaning of the actions in $A_i$, including the communication actions. 
	* Thus, agents *must learn how to interpret the meaning of actions*

* In MARL, we assume that agents do not know any reward functions, but instead they only experience the immediate effects of their own actions. 

* **Open Multi-agent environments** - environments where agents may dynamically enter and leave the environment. 

* A **no-conflict game** is a game where all agents agree on the most-preferred outcome. More formally, where $\forall i,j\in N$
  
  $$
  \underset{\pi}{\text{argmax}} \ U_i(\pi) = \underset{\pi}{\text{argmax}} \ U_j(\pi)
  $$
	* Agents operating in these games tend to be risk-averse, especially when multiple equilibria exist. 

* A **common reward game** is a game where all agents share the same reward function. That is $\forall i, j\in N: R_i = R_j$. 

# Solution Concepts 
* *Defines the [[Game Theory - Strategy|notion]] of "optimal" agent behavior*. 

* We first define the notion of return (see more [[A Unified View on Reinforcement Learning Approaches|here]]). These two definitions are equivalent
	* The **History Based Expected Return** for agent $i$ under policy $\pi$ as the average of the returns of agent $i$ in each possible history 
	  
	  $$
	  \begin{split}
	  U_i(\pi) &= \lim_{t\to\infty} \mathbb{E}_{\hat{h}\sim (\mu,\mathcal{T}, \mathcal{O}, \pi)} \ [u_i(\hat{h}^t)] \\
	  &= \sum_{\hat{h}^t \in \hat{H}} \ P(\hat{h^t}\mid \pi) \ u_i (\hat{h}^t)  
	  \end{split}
	  $$
	
	* The **Recursive Expected Error** is analogous to [[Dynamic Programming for Reinforcement Learning|Bellman backup]]. The expected return is defined under $V_i^\pi$ and $Q_i^\pi$.  $\braket{\cdot}$ denotes concatenation
	  
	  $$
	  \begin{split}
	  V_i^\pi(\hat{h}) &= \sum_{a\in A} \ \pi(a\mid \sigma(\hat{h})) \ Q_i^\pi (\hat{h}, a) \\ 
	  
	  Q_{i}^\pi (\hat{h}, a) &= \sum_{s'\in S} \ \mathcal{T} (s'\mid s(\hat{h}), a ) \ \bigg[R_i(s(\hat{h}), a, s) \ + \gamma \sum_{o'\in O} \ \mathcal{O}(o'\mid a, s') \ V_i^\pi (\braket{\hat{h}, a, s', o'} )\bigg] \\ 
	  
	  U_i(\pi ) &= \mathbb{E}_{s^0 \sim \mu, o^0 \sim \mathcal{O}} \left[V_i^\pi (\braket{s^0, o^0}\right]
	  \end{split}
	  $$

* *Note*: The solution concepts defined below are known [[Complexity Theory|NP-hard]] problems in the general case. The computation of $\epsilon-$Nash equilibria, for example is PPAD complete. 

## Equilibria 
* The **Best Response Policy** is defined as the policy that maximizes the return 
  $$
  \text{BR}_i(\pi_{-i}) = \underset{\pi_i}{\text{argmax}} \ U_i(\braket{\pi_i, \pi_{-i}})
  $$

* In a zero-sum game with two agents, a joint policy $\pi$ is a **minimax solution** if 
  
  $$
  \begin{split}
  U_i(\pi) &= \max_{\pi_i'} \ \min_{\pi_j'} \ U_i(\pi_i',\pi_j') \\ 
  &= \min_{\pi'_j} \ \max_{\pi_i'} \ U_t(\pi_i', \pi_j') \\ 
  &= -U_j(\pi)
  \end{split}
  $$

	* Here the agent's policy is *optimized against an opponent that seeks to minimize the agent's return*
	* In the general case, we can solve this with [[Linear Programming]] by solving the following
	  
	  $$
	  \begin{split}
	  \text{minimize} & \ \ \  \ \ \ U_j \\ 
	  \text{subject to} & \ \ \ \ \ \ \sum_{a_i\in A_i} R_j (a_i,a_j) \ \pi_i(a_i) \\ 
	  & \ \ \ \ \ \  \pi_i(a_i) \ge 0 \\
	  & \ \ \ \ \ \ \sum_{a_i\in A_i} \pi_i(a_i) = 1
	  \end{split}
	  $$


* In a general-sum game with $n$ agents, a joint policy $\pi$ is in **[[Static Games of Complete Information|Nash Equilibrium]]** if  $\forall i, \pi'_i$
  
  $$
  U_i (\pi_i', \pi_{-i})\le U(\pi)
  $$
	* Here *the agent plays a best response to the policies of the other agents*
	* (*Fink, 1964*) There is always a Nash equilibrium in stationary strategies [^fink_1964]
	
[^fink_1964]:  Fink (1964) [Equilibrium in a Stochastic n-person game](https://projecteuclid.org/journals/journal-of-science-of-the-hiroshima-university-series-ai-mathematics/volume-28/issue-1/Equilibrium-in-a-stochastic-n-person-game/10.32917/hmj/1206139508.full)

* A Nash equilibrium may be relaxed to an **$\epsilon$-Nash equilibrium** for $\epsilon > 0$ where  $\forall i, \pi'_i$ 
  
  $$
  U_i(\pi'_i,\pi_{-i}) - U_i(\pi) \le \epsilon 
  $$

	* Every Nash equilibrium is surrounded by a region of $\epsilon$-Nash Equilibria. 
	* *The return for an $\epsilon$-Nash equilibrium need not be close to the return of the actual Nash equilibrium*. Great discontinuities can lead to such a scenario. 
* In a general-sum normal-form game with $n$ agents, let $\pi_c(a)$ be a joint policy which assigns probabilities to joint actions  $a\in A$. Then $\pi_c$ is a **correlated equilibrium** if for every agent $i\in N$ and every action modifier $\xi_i: A_i\to A_i$ 
  
  $$
  \sum_{a\in A} \pi_c(a) \ R_i (\braket{\xi_i(a_i), a_{-i}}) \le \sum_{a\in A} \pi_c(a) \ R_i (a)
  $$

	* The **action modifier** pertains to any possible deviation to the joint policy. 
	* This policy *generalizes Nash equilibria* to allow for policies where actions can be correlated. 
	* Each agent plays a best response and doesn't want to deviate from their joint actions . It is a best response to the conditional distribution $\pi_{-i}(a_{-i}\mid a_i)$ over actions recommended to other agents by $\pi_c$ given $a_{i}$
	* A more general case is a **coarse correlated equilibrium** which requires the inequality hold for an unconditional action modifier -- which is simply a constant action $\xi_i(a)= a_i$. 
		* *Agents must decide before seeing the recommended action, whether to follow the joint policy, assuming the other agents will follow it*. 

## Other Solution Concepts 
* Equilibria , as a solution concept, are limited because 
	* They may be *suboptimal* - they do not correspond to maximized expected returns. 
	* They are *not unique* which can also entail different returns. 
	* They may be *incomplete* in that they do not specify behaviors for off-equilibrium paths. 

* A joint policy $\pi$ is **Pareto dominated** by another joint policy $\pi'$ if 
  $$
  \forall i:  \ U_i(\pi') \ge U_i (\pi) \ \text{and} \ \exists i:\ U_i(\pi') > U_i (\pi)
  $$
  A joint policy that is not Pareto dominated is **Pareto optimal**. The returns of a Pareto optimal policy are also referred to as Pareto optimal. 
	* *No agent can be better off without all other agents being worse off*
	* A solution concept (such as an equilibrium) can be Pareto optimal without being an equilibrium solution. 

* The **social welfare** of a joint policy $\pi$ is defined as 
  
  $$
  W(\pi) = \sum_{i\in N} U_i(\pi)
  $$
  A joint policy is **welfare-optimal** if 
  $$
  \pi \in \underset{\pi'}{\text{argmax}}  \ W(\pi')
  $$

* The **social fairness** of a joint policy $\pi$ is defined as 
  
  $$
  F(\pi ) = \prod_{i\in N} U_i (\pi)
  $$
  
  A joint policy is **fairness-optimal** fi 
    $$
  \pi \in \underset{\pi'}{\text{argmax}}  \ F(\pi')
  $$

* *Among the policies that achieve equal welfare, the policy with the greatest fairness is that which gives equal expected return for each agent*
* Welfare optimality implies Pareto optimality. 

## No-Regret 
* The **regret** of an agent is the *difference between the rewards the agent received and the rewards it could have received from following a different action or policy*. 
  
  It may be defined as follows in terms of rewards and actions 
$$
\text{Regret}_i ^z = \max_{a_i\in A_i} \sum_{e=1}^z \big[R_i(\braket{a_i , a_{-i}^e}) - R_i (a^e) \big]
$$
Or in terms of policies chosen across episodes 
$$
\text{Regret}_i ^z = \max_{a_i\in \Pi_i} \sum_{e=1}^z \big[U_i(\braket{\pi_i , \pi_{-i}^e}) - U_i (\pi^e) \big]
$$


* An agent has **no-regret** if, in the limit of infinitely many episodes, the regret is at most $0$. More formally 
  
  $$
  \forall i : \lim_{z\to \infty } \frac{1}{z}  \ \text{Regret}_i^z \le 0 
  $$

* An agent has **$\epsilon$-no-regret** if for $\epsilon > 0$. 
  $$
  \forall i : \lim_{z\to \infty } \frac{1}{z}  \ \text{Regret}_i^z \le \epsilon
  $$

* *Regret assumes that the actions or policies of the other agents remain fixed in each episode*. 
* When the policies of more than one agent changes, *minimizing regret does not imply maximizing return*. 

# Links 
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer ]] - Ch. 3 - 4