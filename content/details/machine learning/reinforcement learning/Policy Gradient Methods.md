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

* **The Policy Gradient Theorem**. Let $J(\theta)$ be the expected reward and $r(\tau)$ denote the total reward of trajectory $\tau$ following $\pi$, [^2] Then, we have 
$$
\begin{split}
J(\theta) &= E_{\pi_\theta}[r(\tau)] \\ 
\nabla J(\theta) &=  E_{\pi_\theta} [r(\tau) \nabla_\theta \log \pi_\theta (\tau)] \\ 
&= E_{\pi_\theta} \left[r(\tau) \sum_{t=1}^T \nabla_\theta \log \pi_\theta(a_t\mid s_t)\right]
\end{split}
$$

* If we take the expected reward to be the undiscounted value function $v_{\pi_\theta}$ we get the following (the gradient is with respect to $\theta$ as usual)

$$
\begin{split}
J(\theta) &= v_{\pi_\theta}(s) \\ 
\nabla J(\theta) &\propto \sum_{s}\mu(s) \sum_a q_{\pi_\theta}(s,a) \nabla \pi_\theta(a\mid s)
\end{split}
$$

$\mu$ is the on-policy distribution

The proportionality constant $c$ is the average length of an episode in the episodic case and $1$ in the continuous case. [^1]

[^1]: In practice, we don't really care about this because it will be weighted by a step size $\alpha$ anyway.
[^2]: Note, the presented formula generalizes whether or not we use discounting.
### EGLP Lemma
* The **Expected Grad-Log-Prob** lemma is an intermediate result that is applied extensively in policy gradients
* Let $P_\theta$ be a parameterized probability distribution over a random variable $x$, then 
$$
E_{x\sim P_\theta} [\nabla_\theta \log P_\theta (x)] = 0
$$

### Baselines
* We can generalize the policy gradient theorem to include comparison with a **baseline** $b(s)$

$$
\nabla J(\theta) =  E_{\pi_\theta} \left[\sum_{t=0}^T \nabla_\theta \log \pi_\theta (a_t\mid s_t) \ \left(\sum_{t'=t}^T R(s_{t'},a_{t'} ,s_{t'+1} ) - b(s_t)\right)\right]
$$
Where the baseline can be any function as long as it is not dependent on $a$.
* The rationale with baselines is that *it reduces any variance of sample estimates* of the policy gradient
* *The usual choices are either the on-policy distribution $\mu$ or an estimated value $\hat{v}(s)$. 

### Continuing Cases
* For the continuing case, we simply generalize by using the [[A Unified View on Reinforcement Learning Approaches#Average Reward Formulation|average reward formulation]].  The derivation is otherwise the same. 
* In this case, the proportionality becomes an equality.

$$
J(\theta) = \sum_{s}\mu(s) \sum_a q_{\pi_\theta}(s,a) \nabla \pi_\theta(a\mid s)
$$

# Policy Gradient Algorithms
* All of these algorithms rely on the Policy Gradient Theorem
### All Actions Update
* Update using the following rule
$$
\theta_{t+1} = \theta_t +\alpha \sum_a \hat{q}(S_t,a,w)\ \nabla \pi(a\mid S_t,\theta)
$$
### REINFORCE: Monte Carlo Policy Gradient
* Update, at time $t$ only the action $A_t$.
* We redefine $J(\theta)$ as follows. We replace $a$ by the sample $A_t\sim \pi$ and note that $q_\pi(S_t,A_t)$ is the expected return.

$$
\begin{split}
\nabla J(\theta)
&= E_{\pi_\theta} \left[\pi_\theta(a\mid S_t,\theta) \ q_{\pi_\theta}(S_t,a) \frac{\nabla\pi_\theta(a\mid S_t)}{\pi_\theta(a\mid S_t)}\right] \\ 
&= E_{\pi_\theta}\left[q_{\pi_\theta} (S_t,A_t) \frac{\nabla\pi_\theta(a\mid S_t)}{\pi_\theta(a\mid S_t)} \right] \\ 
&= E_{\pi_\theta}\left[G_t \frac{\nabla\pi_\theta(a\mid S_t)}{\pi_\theta(a\mid S_t)}\right] \\
&= E_{\pi_\theta}\left[G_t \nabla \ln \pi_\theta(a\mid S_t)\right]
\end{split}
$$
* The above approach makes it so that actions that are updated frequently are updated in small increments (to balance out the frequency).
* The vector $\nabla \ln \left(\pi_\theta(a\mid S_t,\theta)\right)$ is called the **eligibility vector**
* REINFORCE has *high variance and slow learning* being [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]]. However, it has convergence guarantees.
	* We can add a [[#Baselines|baseline]] to the regular REINFORCE algorithm in order to reduce variance. 

### Actor-Critic Methods
* Act as analogues to [[Temporal Difference Learning]] and [[N-step Bootstrapping]] but for Policy Gradient Methods.
* Rather than have an estimate that solely relies on the full return (as in Monte Carlo approaches such as [[#REINFORCE Monte Carlo Policy Gradient|REINFORCE]]), we instead have an n-step estimate coupled with a learned baseline.

$$
\theta_{t+1} = \theta_t + \alpha \left(G'_t -\hat{v} (S_t,w)\right) \frac{\nabla\pi_\theta(a\mid S_t)}{\pi_\theta(a\mid S_t)}
$$

Where $G_t'$ is a generalization. It could be the one-step return from regular TD, or the n-step return $G_{t:t+n}$ or even an [[Eligibility Traces|eligibility trace]] $G_t^\lambda$. 


# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 13]]
	* 13.2 - proof of the Policy Gradient Theorem for the episodic case. 
	* 13.3 - REINFORCE
	* 13.4 - REINFORCE with Baseline

* [Policy Gradients in a Nutshell](https://towardsdatascience.com/policy-gradients-in-a-nutshell-8b72f9743c5d)
* [[A Unified View on Reinforcement Learning Approaches]]
* [Spinningup -- Intro to Policy Optimization](https://spinningup.openai.com/en/latest/spinningup/rl_intro3.html)