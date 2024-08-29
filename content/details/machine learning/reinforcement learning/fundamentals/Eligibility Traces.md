* *The need for eligibility traces arises in general whenever one tries to learn long-term predictions in an efficient manner*.
* Every result below generalizes from state value functions to action-value functions with the appropriate replacements.
* In practice, implementing eligibility traces are quite efficient since we only need to keep track of and update only the few traces that are significantly greater than $0$.
	* And we use them to complement [[Function Approximation in Reinforcement Learning|function approximation]] for performance reasons.
# Overview
* The **eligibility trace** $z_t\in \mathbb{R}^d$ acts as a *short-term memory vector* that parallels the weights in [[Function Approximation in Reinforcement Learning|function approximation]].
* When a component in $w_t\in \mathbb{R}^d$ participates in estimation, the corresponding component to $z_t$ is bumped up and then begins to fade away based on parameter $\lambda$. 
* Learning occurs in a component of $w_t$ if a non-zero TD-error occurs before the trace falls back to zero. 
* Compared to [[N-step Bootstrapping]], Eligibility traces offer computational advantages. 
	* We no longer need to store $n$ feature vectors, just the $d$-dimensional trace.
	* Learning occurs continually and uniformly rather than being delayed $n$ steps.

* One way to view this is as *an extension of interpolating between Temporal Differencing  and Monte Carlo* methods
	* **Error reduction property**  With updates, the $n$-step return $R_{\Sigma}$ converges a better estimate of the value function as $n\to\infty$.
* Another way is to view this as keeping a temporary record of **which components ( states / actions / components in the weight vector) are eligible for learning changes.** 
	* We are concerned with the TD errors in particular. 
* Eligibility traces make use of **compound updates** -- averaging over simpler updates.

### $\lambda$-return
The **$\lambda$-return** is defined as 
  $$
  G_t^\lambda=(1-\lambda)\sum_{n=1}^\infty\lambda^{n-1}G_{t,t+n}
  $$
  
* Each $n$-step return is weighted with $\lambda^{n-1}$. The whole some is renormalized using the $(1-\lambda)$ term.
* An alternative formulation if we terminate at time $T$ is as follows: 

$$
  G_t^\lambda=(1-\lambda)\sum_{n=1}^T\lambda^{n-1}G_{t:t+n} + \lambda^{T-t-1}G_t
$$
* $\lambda$ is called the **trace decay**. 
	* $\lambda$ controls how much credit we give to earlier states when we perform updates

### Kinds of Traces
* The **accumulating trace** is defined as 
$$
\begin{split}
z_{-1}&=0 \\
z_t &= \gamma \ \lambda z_{t-1} + \nabla \hat{v}(S_t,w_t) \ \ \ 0\le t\le T
\end{split}
$$


* The **action-value form** of the eligibility trace is defined as  

$$
\begin{split}
z_{-1}&=0 \\
z_t &= \gamma \ \lambda z_{t-1} + \nabla \hat{q}(S_t,A_t, w_t) \ \ \ 0\le t\le T
\end{split}
$$

* The **general accumulating trace update for state values** is of the form
  $$
  z_t = \rho_t (\gamma_t\lambda_t z_{t+1} + \nabla \hat{v} (S_t, w_t))
  $$
  Where $\rho_t$ is the importance sampling ratio and we assume varying trace decay $\lambda_t$ and discounting rate $\gamma_t$

* The **general accumulating trace update for action values** is of the form 

$$
z_t = \gamma_t \lambda_t \rho_t z_{t-1} + \nabla\hat{q} (S_t,A_t,w_t)
$$

* The **Dutch Trace** is defined as
$$
z_t = \gamma \lambda z_{t-1} + (1-\alpha \gamma \lambda \ z_{t-1}^T x_t)  x_t
$$
* The **Replacing Trace** is defined on a component-by-component basis on whether the component of the feature vector was $1$ or $0$.

$$
z_{i,t} = 
\begin{cases}
1 & \text{if } x_{i,t} = 1 \\
\gamma\lambda z_{i,t-1} & \text{otherwise}
\end{cases}
$$


* We use replacing traces as approximations of Dutch Traces, which are generally preferred.
* Accumulating Traces are used when there is no theoretical basis for Dutch Traces

### Relation to Monte Carlo
* Eligibility traces can arise even when we use [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]]. 
* A backward view of Monte Carlo can be used to improve performance (for example by using Dutch traces).

# $\text{TD}(\lambda)$  and its variants
* In the **off-line update algorithm**, performing the updates follows the usual [[Off Policy Prediction and Control with Approximation#Semi-Gradient Methods|semi gradient approach]] with $G_t^\lambda$ as the target. 
	* Updates are performed after the episode, possibly in batches.

$$
w_{t+1} = w_t + \alpha \left[G_t^\lambda - \hat{v} (S_t,w_t)\right] \ \nabla \hat{v} (S_t,w_t)
$$

* In $TD(\lambda)$  the eligibility vector is computed using the accumulating trace (see above).
* The weight vector $w$ is then updated using the TD-error and the eligibility trace vector

$$
w_{t+1}=w_t+\alpha\delta_tz_t
$$

* $TD(\lambda)$ is more preferable than the off-line update algorithm because
	* It performs a backward update -- on every step of an episode rather than only at the end. *Estimates are better sooner than later*
	* Its computations are properly amortized -- distributed in time.
	* It can be applied to continuing problems. 
		* $TD(1)$ is a variation of [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]] but applicable for continuous tasks.

* Linear $TD(\lambda)$ converges, but not to the minimum-error vector. For the continuing discounted case:

$$
\overline{\text{VE}}(w_\infty) \le \frac{1-\gamma\lambda}{1-\gamma}\min_w \overline{\text{VE}} (w)
$$


### Truncated return
* In practice, because of the potentially infinite number of terms ,we cannot precisely calculate the above. To compensate, we may include the **truncated $\lambda$ return**. 
  
  $$
  G_{t:h}^\lambda = G_t^\lambda=(1-\lambda)\sum_{n=1}^{h-t-1}\lambda^{n-1}G_{t:t+n} + \lambda^{h-t-1}G_{t:h}
  $$

* It is the weighted average of the [[N-step Bootstrapping|n-step]] return, weighted with $\lambda^{n-1}$
* We perform this using the following update rule 
$$
w_{t+n} = w_{t+n-1} +\alpha\left[G_{t:t+n}^\lambda - \hat{v}(S_t,w_{t+n-1})\right] \ \nabla \hat{v}(S_t,w_{t+n-1})
$$

* Note that no updates were made in the first $n-1$ steps and $n-1$ additional updates were made upon termination.
* The following identity is used for efficient implementation

$$
\begin{split}
G_{t:t+k}^\lambda &= \hat{v}(S_t,w_{t+1}) +\sum_{i=t}^{t+k-1} (\gamma\lambda)^{i-t} \delta'_t \\ 
\delta_t' &= R_{t+1} + \gamma \hat{v} (S_{t+1},w_t) - \hat{v} (S_t,w_{t-1})
\end{split}
$$


* *There is a tradeoff*: $n$ should be large to properly approximate $\lambda$-return, but also small so that updates can be made sooner.

### Online $\lambda$-return 
* We can make better approximations to the offline $\lambda$ update, while making them happen sooner, at the cost of computational complexity.
	* Updates are performed during the episode.
* *On each time step, go back and redo all updates since the beginning, accounting this time step's new data*. 
* The **online $TD(\lambda)$ algorithm** Let $w_t^h$ denote the weights used to generate the value at time $t$ in the sequence up to horizon $h$. The update takes the form 
  $$
  \begin{split}
  w_{t+1}^h &= w_t^h +\alpha\left[G_{t+h}^\lambda -\hat{v}(S_t,w_t^h)\right] \ \nabla \hat{v} (S_t,w_t^h), \ \ \ \ 0\le t <h\le T  \\
  
  w_t &= w_t^t
  \end{split}
  $$
  
* More computational complexity but at the same time more accurate than off-line updates because *it makes use of bootstrapping, that makes the weight vector used more informative*.
* The **true online $TD(\lambda)$ algorithm** [^1] is derived by using the following update rule. Note that it works for the linear case where $\hat{v}(s,w)= w^T x(s)$. 

$$
\begin{split}
w_{t+1} &= w_t + \alpha \delta_t z_t + \alpha (w_t^Tx_t - w_{t-1}^Tx_t)(z_t -x_t) \\ 
x_t &= x(S_t) \\ 
\delta_t &= R_{t+1} + \gamma \hat{v}(S_{t+1}, w_t) - \hat{v}(S_t, w_t) \\ 
z_t &= \gamma \lambda z_{t-1}  + (1-\alpha\gamma z_{t-1}^T x_t) x_t
\end{split}
$$

* The above algorithm gives the same results as the regular online $\lambda$-return algorithm but is less computationally expensive (in terms of performance. In terms of memory, they are still the same.)
	* Note that *it makes use of Dutch traces*.


[^1]: Derivation found in [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto]] but also in a paper by van Seijen et. al, 2016. The general ide ais that if we arrange all the $w_t^h$'s in a matrix, we see that only the diagonal terms of this matrix are important, and we represent each term with the previous diagonal term.

# $\text{SARSA}(\lambda)$
* An extension of [[Temporal Difference Learning#SARSA|SARSA]] but making use of Eligibility traces. We substitute the value function with the state-action function $Q(s,a)$ and the eligibility traces are now over the space of state-action pairs.
* Like SARSA, it is an *on-policy* algorithm.
* *We make use of the $n$-step return as defined in [[On Policy Prediction and Control with Approximation#Episodic Semi-Gradient Control|here]].*
* We can form the **action-value form** of the $\lambda$-return (which just makes use of $q$ instead of $v$ but is otherwise the same as the off-line version)
* The update rule is *mostly the same as the off-line $TD(\lambda)$*, except using the action value form of the TD-error and the action-value form of the eligibility trace,
# Generalization
## Varying $\lambda$. 
* Another (*theoretical*) technique for generalizing the $\lambda$-return is by allowing $\lambda$  and $\gamma$ to vary from step to step. (see [[A Unified View on Reinforcement Learning Approaches#Generalized Discounted Return Formulation|here]] for more on this)
* In this case, we set $\lambda_t$ and $\gamma_t$ as the values used at timestep $t$. The new $\lambda$-return is defined using the state and state-action formulations below

$$
\begin{split}
G_t^{\lambda s} &= R_{t+1} +\gamma_{t+1} ((1-\lambda_{t+1}) \ \hat{v} (S_{t+1}, w_t) + \gamma_{t+1} G_{t+1}^{\lambda s}) \\
G_t^{\lambda a} &= R_{t+1} +\gamma_{t+1} ((1-\lambda_{t+1}) \ \hat{q} (S_{t+1}, A_{t+1}, w_t) + \gamma_{t+1} G_{t+1}^{\lambda a})
\end{split}
$$

* The [[Temporal Difference Learning#Expected SARSA|expected SARSA form]] is defined as follows (using [[Function Approximation in Reinforcement Learning|function approximation]])

$$
\begin{split}
G_t^{\lambda a} &= R_{t+1} +\gamma_{t+1} ((1-\lambda_{t+1}) \ \hat{V} (S_{t+1}) + \gamma_{t+1} G_{t+1}^{\lambda a}) \\ 
\hat{V}_t (s) &= \sum_{a} \pi(a\mid s) \ \hat{q} (s,a,w_t)
\end{split}
$$

* One *rationale* for this is to give states whose value we are highly certain of, more credit (higher eligibility) for the return.

## Incorporating Control Variates
* See [[N-step Bootstrapping#Control Variates|here]] for more about control variates. 
* *Rationale*: The result here gives us an eligibility trace which, when combined with semi-gradient descent, *forms a general $TD(\lambda)$ algorithm that can be applied to on/off-policy data*. 
	* Caveat: It is not necessarily stable as an off-policy algorithm. It also has high variance even with importance sampling.
* *Rationale*: We cannot directly apply [[Importance Sampling]] to $\lambda$-returns so instead we directly use control variates. 
### Using State-Values 
* Doing so generalizes the return as 

$$
G_t^{\lambda s} = \rho_t\left(R_{t+1} +\gamma_{t+1} ((1-\lambda_{t+1}) \ \hat{v} (S_{t+1}, w_t) + \gamma_{t+1} G_{t+1}^{\lambda s})\right) + (1-\rho_t) \hat{v} (S_t,w_t)
$$

Where $\rho_t$ is the single-step importance sampling ratio. 


* The above can be *approximated using TD-errors*

$$
\begin{split}
\delta_t^s &= R_{t+1} +\gamma_{t+1} \hat{v}(S_{t+1}, w_t) - \hat{v}(S_t,w_t) \\ 
G_{t}^{\lambda s} &\approx \hat{v}(S_t,w_t) + \rho_t \sum_{k=t}^\infty \delta_k^s \prod_{i=t+1}^k \gamma_i\lambda_i \rho_i
\end{split}
$$

Where the approximation becomes exact if the value function does not change. [^2]

* A single step of a forward view is then given as 
$$
\begin{split}
w_{t+1} &= w_t+\alpha (G_t^{\lambda s} - \hat{v} (S_t,w_t)) \nabla \hat{v} (S_t, w_t) \\ 
&\approx w_t + \alpha \rho_t \left(\sum_{k=t}^\infty \delta_k^s \prod _{i=t+1}^k \gamma_i \lambda_i \rho_i \right) \nabla\hat{v} (S_t, w_t)
\end{split}
$$

* The sum of the forward view updates is given as 

$$
\sum_{t=0}^\infty (w_{t+1}-w_t) = \sum_{k=0}^\infty \alpha\delta_k^s \sum_{t=0}^k \rho_t\nabla \hat{v} (S_t,w_t) \prod _{i=t+1}^k \gamma_i \lambda_i \rho_i 
$$

And this sum is *of the form a sum of a backward-view TD update* because we can perform the update as an eligibility trace using  the general accumulating trace update for state values. (see above). [^3] We get that for the general accumulating trace $z_k$

$$
\sum_{t=0}^\infty (w_{t+1} - w_t) = \sum_{k=0}^\infty \alpha\delta_k^s z_k
$$


[^2]: This follows just by expanding the recursive formula given from the exact value of $G_t^{\lambda s}$. 

### Using Action-Values
* For the action-value case the derivation is similar. We get that
$$
G_t^{\lambda a} = R_{t+1} + \gamma_{t+1} (\hat{V}_t(S_{t+1})+\lambda_{t+1}\rho_{t+1} \left[G_{t+1}^{\lambda a} -\hat{q}(S_{t+1},A_{t+1}, w_t) \right])
$$

Where $\hat{V}_t$ is given [[#Varying $ lambda$.|here]]. 

* This gives an approximation using the expectation form of the action-based TD-error
$$
\begin{split}
\delta_t^a &= R_{t+1} +\gamma_{t+1} \hat{V}(S_{t+1}, w_t) - \hat{q}(S_t, A_t,w_t) \\ 
G_{t}^{\lambda a} &\approx \hat{q}(S_t,A_t,w_t) + \sum_{k=t}^\infty \delta_k ^n \prod_{i=t+1}^k \gamma_i \lambda_i \rho_i
\end{split}
$$

* This approximation becomes exact if the approximate value function does not change.
* Similar to the case for state-values, we can derive a form that uses the generalized eligibility trace for action values (see [[#Kinds of Traces|here ]])

### Relation to Monte Carlo
* At $\lambda=1$, it behaves like Monte-Carlo methods except that eligibility traces still perform bootstrapping. However, the dependence on estimates cancels out in the expected values.
* Methods that achieve exact equivalence require **provisional weights** to keep track of updates made but may need to be retracted or emphasized depending on actions later. These are called **PTD algorithms**.
* At $\lambda<1$, the [[Off Policy Prediction and Control with Approximation#Divergence|deadly triad]] applies.
# Watkins' $Q(\lambda)$
* Extends Q-learning to make use of eligibility traces. 
* One caveat of this is that, instead of looking ahead all the way to the end, it only looks ahead *as far as the action after the first exploratory action* (or to the episode's end if none exist)
* Whenever a non-greedy action is taken, the eligibility trace at that point is set to $0$.
* *Note:* This relies on the action sequence of the behavior policy having few exploratory actions, as otherwise this performs no better than one-step Q-learning.
* *Watkins $Q(\lambda)$ is a crude way to perform off-policy tracing.* However, we must consider the following:
	* Use Importance sampling to assign credit for actions, since actions are taken based on a probability distribution so following the greedy action is dependent on this probability.
	* It does not actually bootstrap since it cuts off estimation after the first non-greedy action is taken.
# Tree Backup with Eligibility Traces
* See [[N-step Bootstrapping#Tree Backup Algorithm|here]] for more on the tree backup algorithm.
* The return is calculated as 

$$
\begin{split}
G_{t}^{\lambda a} &= R_{t+1} +\gamma_{t+1} \left( \hat{V} _t(S_{t+1}) +\lambda_{t+1} \pi (A_{t+1}\mid S_{t+1})  \left(G_{t+1}^{\lambda a} -\hat{q} (S_{t+1}, A_{t+1}, w_t) \right)\right) \\
&\approx \hat{q}(S_t,A_t, w_t) + \sum_{k=t}^\infty \delta_k^n \prod_{i=t+1} ^k \gamma_i\lambda_i \pi (A_i\mid S_i)
\end{split}
$$
Where $\delta_k$ is the TD error defined [[#Using Action-Values|here]]. 

* The eligibility trace update is defined using
$$
z_t =\gamma_t\lambda_t \pi(A_t\mid S_t) z_{t-1} + \nabla \hat{q} (S_t,A_t, w_t)
$$
* And then apply the usual update rule defined in $TD(\lambda)$.

# Stable Off-Policy Methods
### $GTD(\lambda)$
* **$GTD(\lambda)$** is the counterpart to [[Off Policy Prediction and Control with Approximation#Gradient-TD Methods|TDC]] . The update rule is given as 

$$
\begin{split}
w_{t+1} &= w_t  + \alpha \delta_t^s z_t -\alpha \gamma_{t+1} (1-\lambda_{t+1} ) (z_t^Tv_t)x_{t+1} \\
v_{t+1} &= v_t + \beta\delta_t^s z_t -\beta (v_t^Tx_t)x_t
\end{split}
$$

Where $v\in \mathbb{R}^d$ is a vector of the same dimension as $w$, initialized to $v_0$, and $\beta>0$ is a second step-size parameter.

And we use $\rho$ as per-decision importance sampling
$z_t$ is the general accumulating trace for state values
$\delta_t^s$ is the TD-error is defined in [[#Using State-Values|here]].

* $TD(\lambda)$ is often faster than $GTD(\lambda)$ when both algorithms converge.

### $GQ(\lambda)$
* The Gradient TD algorithm for action values with eligibility traces.
* It learns $w_t$ such that $\hat{q}(s,a,w-t) = w_t^Tx(s,a) \approx q_\pi (s,a)$ from off-policy data. 
* If the target policy is $\epsilon$-greedy or biased towards the greedy policy, then $GQ(\lambda)$ can be used for control.
* The update is given as

$$
\begin{split}
w_{t+1} &= w_t  + \alpha \delta_t^s z_t -\alpha \gamma_{t+1} (1-\lambda_{t+1} ) (z_t^Tv_t)\bar{x}_{t+1} \\
\bar{x}_t &= \sum_a \pi(a\mid S_t) \ x(S_t,a) \\ 
\delta_t^a &= R_{t+1} +\gamma_{t+1} w_t ^T \bar{x}_{t+1} -w_t^T x_t
\end{split}
$$

Where $z_t$ is defined using the general accumulating trace for state values, and the rest follows from [[#$GTD( lambda)$|GTD]]$(\lambda)$ including updating $v_t$.

### $HTD(\lambda)$
* A hybrid state-value algorithm combining $GTD(\lambda)$ and $TD(\lambda)$. 
* It is a *strict generalization of $TD(\lambda)$ to off policy learning* -- if the behavior happens to be the target policy, then $HTD(\lambda)$ is the same as $TD(\lambda)$.

$$
\begin{split}
w_{t+1} &= w_t  + \alpha ((z_t-z_t^b)^Tv_t) (x_t-\gamma_{t+1}x_{t+1}) \\
v_{t+1} &= v_t + \beta \gamma_t^s z_t - \beta ({z_t^b}^Tv_t)(x_t -\gamma_{t+1} x_{t+1}) & v_0 = 0 \\ 
z_t &= \rho_t(\gamma_t \lambda z_{t-1} + x_t) & z_{-1} = 0 \\
z_t^b &= \gamma_t \lambda_t z_{t-1}^b +x_t & z_{-1}^b =0
\end{split}
$$

* We have $\beta>0$ as an additional step-size parameter and $v_t$ is a second set of weights.
* $z_t^b$ acts as a second set of accumulating eligibility traces for the behavior policy. 
	* $z_t^b=z_t$ if all $\rho_t=1$.

### Emphatic $TD(\lambda)$
* An extension of [[Off Policy Prediction and Control with Approximation#Emphatic TD Methods|Emphatic TD]] to eligibility traces. 
* It retains strong off-policy convergence guarantees while allowing bootstrapping.
* *Downsides*: High variance and slow convergence

$$
\begin{split}
w_{t+1} &= w_t +\alpha \delta_t z_t \\
\delta_t &= R_{t+1} +\gamma _{t+1} w_t^T x_{t+1} -w_t^Tx_t \\ 
z_t &= \rho_t (\gamma_t\lambda_t z_{t-1} +M_tx_t) & z_{-1}=0 \\ 
M_t &= \lambda_tI_t +(1-\lambda_t)F_t \\ 
F_t &= \rho_{t-1}\gamma_t F_{t-1} + I_t & F_0 =v(S_0)
\end{split}
$$
* [[Off Policy Prediction and Control with Approximation#Emphatic TD Methods|Emphasis]] is generalized with $M_t\ge 0$
* $F_t\ge 0$ is termed the **followon trace**
* $I_t\ge 0$ is the interest as defined [[Off Policy Prediction and Control with Approximation#Emphatic TD Methods|here]]. 
# Links
* [[Temporal Difference Learning]] - for more info on the basic case $\text{TD}(0)$. 
* [[N-step Bootstrapping]] - another way to generalize temporal difference learning. 
* [[Monte Carlo Methods in Reinforcement Learning]] - for more on Importance sampling
* [[A Unified View on Reinforcement Learning Approaches]]

* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 12]]
	* 12.2 - $TD(\lambda)$
	* 12.5 - True online $TD(\lambda)$ 
	* 12.6 - for a proof on backwards Monte Carlo
	* 12.7 - SARSA$(\lambda)$ as well as True Online SARSA$(\lambda)$.
	* 12.8 - a more detailed view in integrating Off-Policy traces with Control Variates