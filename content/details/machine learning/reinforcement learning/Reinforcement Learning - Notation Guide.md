* $t$ - discrete time step
* $T, \mathcal{T}(t)$ - final time step of an episode, or of the episode including time step $t$. 
<br>
* $\tau$ - a trajectory.
* $S_t, s_t, s$ - state at time  $t$
* $A_t, a_t, a$,- action at time $t$
* $\mathcal{S}$ - set of all non-terminal states
* $\mathcal{S}^+$ - set of all states (including terminal states).
* $\mathcal{A}$ - set of all actions
* $\mathcal{A}(s)$ - set of all actions available from state $s$.
<br>
* $N_t(a)$ - number of times an action is taken prior to time $t$.
* $\eta(s)$ - expected number of visits of to state $s$. 
<br>
* $r_t$- reward at time $t$
* $R(S_t,A_t,S_{t+1})$ - reward obtained by going from $S_t$ to $S_{t+1}$ via action $A_t$.
* $R_t$ - estimate of a reward at time $t$.
* $\mathcal{R}$ - set of all possible rewards.
* $r(\tau)$ - total reward obtained in a trajectory
* $r(\pi)$ - average reward from following policy $\pi$ 
* $r(s,a)$ - expected immediate reward obtained from state $s$ taking action a$a$.
* $r(s,a,s')$ - expected immediate reward obtained on transitioning from $s$ to $s'$ via $a$
<br>
* $p(s',r\mid s, a)$ - (hidden) environment dynamics. The probability of going to $s'$ and receiving reward $r$ by taking action $a$ from state $s$.
* $\pi$ - policy
* $\beta(a\mid s)$ - in the context of off-policy learning, the behavior policy.
* $\pi(s)$ - \action taken under (deterministic) policy $\pi$ at state $s$
* $\pi(a\mid s)$ - probability of taking action $a$ in state $s$.
* $\pi_t(a)$ - probability of selecting action $a$ at time $t$.
* $\pi_\ast$ - optimal policy
* $\pi_\theta$ - policy parameterized by $\theta$.
<br>
* $\epsilon$ - in an $\epsilon$-greedy policy, denotes the degree of exploration.
* $\alpha,\beta$ - step size parameters
* $\gamma$ - discount rate parameter
* $\gamma_t$ - discount at time $t$.
* $\lambda$ - trace decay rate for eligibility traces.
* $\lambda_t$ - trace decay at time $t$.
<br>
* $v_\pi(s)$ - true state value function for policy $\pi$
* $v_\ast(s)$ - optimal true value function.
* $q_\pi(s,a)$ - true state-action value function for policy $\pi$. 
* $q_\ast(s,a)$ - true optimal state-action value function.
* $(B_\pi v)(s)$ - Bellman operator for value function $v_\pi$
* $A_\pi(s,a)$ - the advantage function for $\pi$ 

* $V_t, V^{\pi}_t$ - estimate for state value function at time $t$ for policy $\pi$ derived from bootstrapping
* $\overline{V_t}, \overline{V_t^\pi}$ - expected approximate action value at time $t$ for policy $\pi$
* $Q_t, Q_t^\pi$ - estimate for state-action value function at time $t$ for policy $\pi$ derived from bootstrapping
* $\hat{V}_t, \hat{V}_t^\pi$ - expected approximate action value at time $t$ for policy $\pi$
<br>
* $G_t$ - return at time $t$.
* $h$ - horizon. the time step we look up to during a forward view.
* $G_{t:t+n}$ - n-step return from $t+1$ to $t+n$.
* $\overline{G_{t:h}}$ - flat return (undiscounted, uncorrected).
* $G_t^\lambda$ - $\lambda$- return.
* $G_{t:h}^\lambda$ - truncated , corrected $\lambda$ return.
* $G_{t}^{\lambda s},G_{t}^{\lambda a}$ - $\lambda$-return, corrected by estimated state or action vlaue.
<br>
* $\mu(s)$ - on-policy distribution over state $s$.
* $\mu$ - vector of all $\mu$'s. 
* $\mu_\pi$ - the steady state distribution following the average reward formulation of the return.
* $\rho_t$ - importance sampling ratio, taken to be the per-step importance sampling ratio.
* $\rho_{t:T}$ - importance sampling ratio from time $t$ to $T$.
<br>
* $U_t$ - target for estimate at time $t$.
* $\delta_t$ - temporal difference error at $t$.
* $\delta_t^a, \delta_t^s$ - state and action specific forms of the TD error
* $\overline{\delta_w}(s)$ - Bellman error.
* $\delta_w, \text{BE}$ - Bellman error vector
<br>
* $w,v$ - $d$ dimensional vector underlying an approximate value function.
* $\hat{v}(s,w)$ - approximate value of state $s$  given parameters $w$.
* $\hat{q},(s,a, w)$ - approximate value of action pair $s,a$ given $w$.
* $x(s)$ - feature vector visible when in state $s$.
* $x(s,a)$ - feature vector visible when in state-action pair
* $z_t$ - eligibility trace
<br>
* $J(\theta)$ - performance measure using the parameter vector $\theta$.
* $b(s_t)$ - baseline function. Assumed to only be dependent on the state estimate.
* $\overline{VE}$ - mean square value error.
* $||v||_\mu^2$ - $\mu$ weighted square norm of the value function $\sum_{s\in S}\mu(s) \ v(s)^2$
* $\overline{\text{BE}}(w)$ - mean squared Bellman error
* $\overline{\text{PBE}}(w)$ - mean squared Projected Bellman error.
* $\overline{\text{TDE}}(w)$ - mean squared Temporal Difference error.
* $\overline{\text{RE}}(w)$ - mean squared Return Error.
<br>
* $D_t$ - experience replay.
* $e_t$ - an episode step 
* $\beta(s,a)$ - behavior distribution 