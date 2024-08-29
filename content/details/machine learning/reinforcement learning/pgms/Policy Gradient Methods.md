# Characterization
* Let $\theta\in\mathbb{R}^d$ be a policy's parameter vector, and $\pi_\theta = \pi(a\mid s,\theta) = P(A_t=a\mid S_t=s, \theta_t = \theta)$ be the probability an action $a$ is taken given state $s$ and parameter $\theta$ at time $t$. 
	* Assume the policy is [[Differential Calculus|differentiable]] with respect to its parameters. 
	* To ensure [[The Exploitation-Exploration Trade-Off|exploration]], we generally require policies never become deterministic.
* The **performance** of a policy is calculated with respect to $J(\theta)$. *The goal is to maximize performance* using gradient ascent

$$
\theta_{t+1} = \theta_t + \alpha \widehat{\nabla J(\theta_t)}
$$

* Methods that follow this are **policy gradient methods**
* **Actor-Critic methods** learn both the policy (actor) and the value function (critic) 
### Why Policy Gradient Methods?
* *Sometimes the policy is a simpler function to approximate*.
* We can also generalize well to *continuous actions* or stochastic policies.
* It may also be a good way of injecting [[Bayesian Statistics#Priors|prior]] knowledge about the policy.
* With a continuous parameterization, the action probabilities change smoothly so that there is less variance in the updating. We have *stronger convergence guarantees*. 
### Parameterization
* *For discrete and not-too-large action spaces*, we form a parameterized numerical preference $h(s,a,\theta)$ for every state-action pair.
	* The action preferences may be computed using any form of [[Supervised Learning|supervised learning]] technique.
	* The **softmax in action preferences** applies softmax to obtain a probability distribution as follows

$$
\pi(a\mid s,\theta) = \frac{e^{h(s,a,\theta)}}{\sum_be^{h(s,b,\theta)}}
$$

* One advantage to using the softmax  on action preferences is that policies can approach a deterministic policy.
	* *Using softmax on action values does not guarantee convergence to an optimal policy*. It only converges to the true values of the action values.
	* Softmax in action preferences drives the parameters towards the optimal stochastic policy
	* It also enables selecting actions according to arbitrary probabilities.
* *For continuous cases we can parameterize by using a [[Random Variables and Probability Distributions|probability distribution]]* instead.
	* In such a case, we typically want the probability distribution itself to be parameterized on the state  and/or action to be taken.
	* *We usually have parameterizations be dependent on even more parameterizations*.

# Policy Gradient Theorem
* The Policy Gradient Theorem *guarantees that we can perform gradient ascent on the parameterized policy without any knowledge of the model's dynamics* or the initial distribution of states.
	* This arises partly because when we calculate the gradient, any parameterization of the environment would not have a dependence on $\theta$

* **The Policy Gradient Theorem**. Let $J(\theta)$ be the expected reward. If we take the expected reward using the undiscounted value function $v_{\pi_\theta}$ [^2]we get the following (the gradient is with respect to $\theta$ as usual)

$$
\begin{split}
J(\theta) &= \sum_{s\in S} \mu(s) v_\pi(s)\\ 
\nabla J(\theta) &\propto \sum_{s}\mu(s) \sum_a q_{\pi_\theta}(s,a) \nabla \pi_\theta(a\mid s)\\ 
&= \mathbb{E}_{s\sim \mu_(s), a\sim \pi_\theta}[q_\pi(s,a) \nabla_\theta \ln \pi_\theta(a\mid s)] \\ 
&= \mathbb{E}_\pi [q_\pi(s,a) \nabla_\theta \ln \pi_\theta(a\mid s)]
\end{split} 
$$
$\mu$ is the on-policy distribution

The proportionality constant $c$ is the average length of an episode in the episodic case and $1$ in the continuous case. [^1] [^2]  [^3]

The last line is just a way to abbreviate the notation.

[^1]: In practice, we don't really care about this because it will be weighted by a step size $\alpha$ anyway.
[^2]: [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto]] use $v_\pi$ but if we are measuring expected reward, we should average over all the states.  The reason why we can just sum over $v_\pi$ is because the environment is Markovian so we can simply get "all trajectories" just from using any possible starting states. 
[^3]: The $\ln$ part of the formula follows by multiplying the RHS of the equation with $\frac{\pi_\theta(\alpha\mid s)}{\pi_\theta(\alpha\mid s)}$.

### EGLP Lemma
* The **Expected Grad-Log-Prob** lemma is an intermediate result that is applied extensively in policy gradients
* Let $P_\theta$ be a parameterized probability distribution over a random variable $x$, then 
$$
\mathbb{E}_{x\sim P_\theta} [\nabla_\theta \ln P_\theta (x)] = 0
$$

### Baselines
* We can generalize the policy gradient theorem to include comparison with a **baseline** $b(s)$

$$
\nabla J(\theta) =  \mathbb{E}_{\pi_\theta} \left[\sum_{t=0}^T \nabla_\theta \ln \pi_\theta (a_t\mid s_t) \ \left(\sum_{t'=t}^T R(s_{t'},a_{t'} ,s_{t'+1} ) - b(s_t)\right)\right]
$$
Where the baseline can be any function as long as it is not dependent on $a$.
* The rationale with baselines is that *it reduces any variance of sample estimates* of the policy gradient.
* *The usual choices are either the on-policy distribution $\mu$ or an estimated value $\hat{v}(s)$. 

* The baseline does not introduce bias precisely because of the [[#EGLP Lemma]]
* The baseline reduces variance based on the [[Statistical Estimators#Bias-Variance Tradeoff|bias variance tradeoff]]. 
	* In fact, we can view the variance of the above as a sum of squares that can be decomposed with the bias-variance decomposition. [^4].  
	* In line with that, we have the common choice of $\hat{v}(s)$ as a sort of MLE.
	* *The tradeoff applies, we reduce variance at the cost of adding bias*. 

[^4]: see more [here](https://danieltakeshi.github.io/2017/03/28/going-deeper-into-reinforcement-learning-fundamentals-of-policy-gradients/)  for showing the baseline does not introduce bias.

### Baselined Discounting 
* If we want to apply discounting the baseline has to satisfy 

$$
b(s_t) \approx \mathbb E [r _1 + \gamma r_{t+1} + \dots +\gamma^{T-1-t}r_{T-1}]
$$

### Continuing Cases
* For the continuing case, we simply generalize by using the [[A Unified View on Reinforcement Learning Approaches#Average Reward Formulation|average reward formulation]].  The derivation is otherwise the same. 
* In this case, the proportionality becomes an equality.

$$
J(\theta) = \sum_{s}\mu(s) \sum_a q_{\pi_\theta}(s,a) \nabla \pi_\theta(a\mid s)
$$
### Advantage function
* The **advantage function** is defined as 

$$
A_\pi (s,a) = q_\pi(s,a) - v_\pi (s) 
$$
Intuitively, it tells us how better action $a$ is compared to the average action taken on  state $s$.

* We  can reformulate $J(\theta)$ using the advantage function (see [[#The General Policy Gradient Theorem]]). 
* The advantage function formulation is equivalent to the [[#Baseline|baselined formulation]] because 
	* $\mathbb E \left[ \sum_{t}^T r_{t}\right]= q_\pi(s_t,a_t)$  which follows by definition of $q_\pi$. 
	* $\mathbb E \left[  \sum_{t}^T b(s_t)\right] = v_\pi(s_t)$  which must be asserted as true.

* In general [^Kakade_Langford_2002], we can frame the expected return of a policy $\bar{\pi}$ in terms of  the advantage over $\pi$ accumulated over time steps. 
  
  $$
  \eta(\bar\pi) = \eta(\pi)+ \sum_{s} \mu_\pi(s)\sum_{a} \bar{\pi} (a\mid s) A_\pi (s,a)
  $$

	* An important corollary: *Any policy that has a non-negative advantage at every state is guaranteed to increase the policy performance or leave it constant*
	* In an approximate setting, we may encounter errors for which the expected advantage of some state is negative. A local approximation is then given as follows 
	  
	  $$
	  L(\bar{\pi}) = \eta(\pi)+ \sum_{s} N(s)\sum_{a} \bar{\pi} (a\mid s) A_\pi (s,a)
	  $$
	  
	  If $\pi_\theta$ is parameterized and differentiable on $\theta$, then we have that 
	  
	  $$
	  \begin{split}
	  L_{\pi_\theta}(\pi_\theta) &= \eta(\pi_\theta) \\ 
	  \nabla_\theta L_{\pi_\theta} &= \nabla \eta(\pi_\theta)
	  \end{split}
	  $$
	  
	  Which means that a sufficiently small step that improves $L$ will also improve $\eta$.
	  
  
  
  

[^Kakade_Langford_2002]: Kakade and Langdord (2002). [Approximately optimal approximate reinforcement learning](https://people.eecs.berkeley.edu/~pabbeel/cs287-fa09/readings/KakadeLangford-icml2002.pdf)

# The General Policy Gradient Theorem
* We can generalize the Policy Gradient Theorem as follows. Let $J(\theta)$ be the performance measure, specifically defined as the expected total reward

$$
J(\theta) = \nabla_\theta \mathbb{E} \left[\sum_{t=0}^\infty r_t\right]
$$

* *All policy gradient theorems follow the following form*

$$
J(\theta) =  \mathbb{E} \left[ \sum_{t=0}^\infty \Psi \nabla_\theta \ln \pi_\theta (a_t\mid s_t) \right]
$$
$\Psi$ depends on our algorithm.
* $\sum_{t=0}^\infty r_t$ - total reward of the trajectory.
* $\sum_{k=t}^\infty r_k$ - reward following action $a_t$
* $\sum_{k=t}^\infty r_k -b(s_t)$  - baselined reward after action $a_t$
* $q_\pi(s_t,a_t)$ - state-action value function
* $A_\pi(s_t,a_t)$ - advantage function
* $r_t+V_\pi(S_{t+1})-V_\pi(s_t)$ - TD residual.

# Topics
* [[Policy Gradient Method Algorithms]]

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 13]]
	* 13.2 - proof of the Policy Gradient Theorem for the episodic case. 
	* 13.3 - REINFORCE
	* 13.4 - REINFORCE with Baseline

* [Policy Gradients in a Nutshell](https://towardsdatascience.com/policy-gradients-in-a-nutshell-8b72f9743c5d)
* [Spinningup -- Intro to Policy Optimization](https://spinningup.openai.com/en/latest/spinningup/rl_intro3.html)
* [Going Deeper into Reinforcement Learning - Fundamentals of Policy Gradient Methods](https://danieltakeshi.github.io/2017/03/28/going-deeper-into-reinforcement-learning-fundamentals-of-policy-gradients/)
* [Lil'Log Policy Gradient Algorithms](https://lilianweng.github.io/posts/2018-04-08-policy-gradient/)


* [[A Unified View on Reinforcement Learning Approaches]]
