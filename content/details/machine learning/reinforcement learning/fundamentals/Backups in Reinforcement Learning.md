# Definition
* A backup is an operation that performs an update on the [[The Setting for Reinforcement Learning|value function]] 
* We may divide backups based on the following:
	* Whether or not they update state values or action values (i.e., whether they use $q$ or $v$).
	* Whether or not they update the value of the optimal policy or an arbitrary policy (i.e., whether they use $\pi$ or $\pi_\ast$). 
	* Whether or not they operate on all possible successors (full / expected) or a sample of successors (sample backup).

* The equation for performing a backup is as follows 
  $$
  \begin{split}v_\pi(s)&=\sum_{a}\pi(a\mid s) \sum_{s',r}p(s',r\mid s,a)  \left[r + \gamma v_\pi(s')\right] \\ 
  q_\pi(s,a) &=  \sum_{s', r} p(s',r\mid s, a)\left[r + \gamma \sum_{a'\in\mathcal{A}} \pi(a'\mid s') \ q_\pi(s',a')\right] \\ 
  v_{\pi}(s) &= \sum_{a} \pi(a\mid s) \ q_\pi (s, a) \\ 
  q_{\pi}(s,a) &= \sum_{s',r} p(s',r\mid s,a)\left[ r+\gamma \cdot v_\pi(s')\right]
  \end{split}
  $$
  
  Where $p$ is the [[Markov Processes in Machine Learning|dynamics]] function
  
  We can write the above in a more compact manner
  $$
  \begin{split}
  v_\pi(s) &= \mathbb{E}_{a\sim \pi(s)}  \ [q_\pi(s,a)] \\
  q_\pi(s,a) &= \mathbb{E}_{s',r'\sim p(s,a)} \ [r + \gamma \cdot v_\pi(s')] 
  \end{split}
  $$
  Where $\pi(s)$ and $p(s,a)$ are marginal distributions given the provided parameters.

* The **optimal Bellman equations** describe the optimal policy $\pi_\ast$.
  $$
	\begin{split}
	v_\ast(s)&= \max_{a} \sum_{s',r} p(s',r\mid s, a) \ \left [r + \gamma v_\ast(s')\right] \\ 
	q_\ast(s,a) &=  \sum_{s', r} p(s',r\mid s, a)\left[r + \gamma \max_{a'} \  q_\ast(s',a')\right]   \\ 
	v_\ast(s) &= \max_a  \ q_\ast(s,a) \\ 
	q_\ast(s,a) &= \sum_{s', r} p(s',r\mid s, a)\left[r + \gamma \ v_\ast(s') \right]
	\end{split}
	$$
* **Full / Expected Backups** are more precise but at the cost of requiring more computations. For a given state, they backup based on all successors of this state.
	* For stochastic models, we perform the backup using the expected values of the state / action. 
	* These are what we use for [[Dynamic Programming for Reinforcement Learning|Dynamic Programming]]-based approaches
* **Sample backups** are cheaper computationally, but at the cost of having sampling errors (i.e., they are inaccurate). For a given state, they backup based on a sample of the successor states.
	* These are what we use for [[Temporal Difference Learning]] approaches.

* The **Bellman operator** applies to a value function $v$ and is defined as 
  
  $$
  (B_\pi v)(s) = \sum_a\pi(a\mid s) \sum_{s',r} p(s',r\mid s,a)\left[r + \gamma v(s')\right]
  $$
  
# Typology of Updates
| Approach | Description | 
| --- | --- | 
| [[Dynamic Programming for Reinforcement Learning#Policy Evaluation\|Policy Evaluation]] | Expected update on $v_\pi(s)$ | 
| [[Dynamic Programming for Reinforcement Learning#Value Iteration\|Value Iteration]] | Expected update on $v_\ast(s) |
| Q-Policy Evaluation | Expected update on $q_\pi(s,a)$ |
| Q-Value Iteration | Expected update on $q_\ast(s,a)$ | 
| [[Temporal Difference Learning\|TD-0]] | Sample Update on $v_\pi(s)$ |
| ??? | Sample update on $v_\ast(s)$ |
| [[Temporal Difference Learning#SARSA\|SARSA]] | Sample update on $q_\pi(s,a)$ | 
| [[Temporal Difference Learning#Q-Learning\|Q-learning]] | Sample update on $q_\ast(s,a)$ |
* When performing an expected update on a stochastic problem, it is recommended to use [[A Unified View on Planning and Learning#Prioritized Sweeping]].
# Average Reward Bellman Equations
* For the following, assume we are dealing with [[A Unified View on Reinforcement Learning Approaches#Average Reward Formulation|average reward context]]. *Notice; we just replaced all $r$ with $r-r(\pi)$. For the optimality equations, we replaced all discounting.*
  
  $$
  \begin{split}
  v_\pi(s)&=\sum_{a}\pi(a\mid s) \sum_{s',r}p(s',r\mid s,a)  \left[r-r(\pi) + \gamma v_\pi(s')\right] \\ 
  q_\pi(s,a) &=  \sum_{s', r} p(s',r\mid s, a)\left[r - r(\pi) + \gamma \sum_{a'\in\mathcal{A}} \pi(a'\mid s') \ q_\pi(s',a')\right] \\
  v_\ast(s)&= \max_{a} \sum_{s',r} p(s',r\mid s, a) \ \left [r - \max_\pi r(\pi) + v_\ast(s')\right] \\ 
	q_\ast(s,a) &=  \sum_{s', r} p(s',r\mid s, a)\left[r -\max_\pi r(\pi)+ \  \max_{a'}q_\ast(s',a')\right]
  \end{split}
  $$

# Hamilton-Jacobi-Bellman Equations 
* The **Hamilton-Jacobi-Bellman** (HJB) equations can be viewed as a generalization of the Bellman equations to the continuous case 

$$
\gamma v _\pi(s) = \max_{u\in U} \left( \ r(s,u) + \nabla v_\pi (s) \cdot g(s,u)\right)
$$
Where $r(s,u)$ is the instantaneous reward function given state $s$ and control vector $u$.

And $g$ is the law of motion for the state (analogous to the environment's dynamics) [^1]


[^1]: TODO: Move this to the appropriate location

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto]]
	* Ch. 3 - introduction of Bellman backups
	* Ch. 8.5 - Types of Backups