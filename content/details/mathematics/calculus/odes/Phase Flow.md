* A **one parameter [[Fundamental Constructs of Group Theory|group]] of transformations** of a set is an [[Group Action|action]] on the set by the group of all real numbers .
  
  We denote the one parameter group of transformations parameterized by $t$ as $\set{g^t}$ 
  
  For any $s,t\in \mathbb{R}$ 
  $$
  \begin{split}
  g^{s+t} &= g^s g^t \\ 
  g^{-t} &= (g^t)^{-1}
  \end{split}
  $$
  We call the transformation $g^t$ as the **transformation in time** $t$. 
  
  In the group, we define $g^0$ in the obvious way -- as the "do nothing transformation". 
  
  We also call a one parameter group of transformations  a **phase flow** within the phase space $M$. [^phase_flow].

* One parameter groups of transformations can be thought of as *equivalents to two sided deterministic processes* where we map the phase space onto itself. In particular, we map states to future states (i.e., for $g^tx$, the state of the system at time $t$ starting from $x$)
	* It is easy to show that the group properties hold for such a transformation defined on the phase space. 
* The [[Permutations and Orbits|orbits]] of phase flow are called the **phase curves**. 


[^phase_flow]: Imagine the phase space as a fluid map. A phase flow maps each particle in the fluid to its future state. 


* If the surface is a smooth manifold, then we additionally require that the phase flow  be a [[Diffeomorphism]].

* The **phase velocity vector** of the flow $\set{g^t}$ at the point $x$ is the velocity with which $g^tx$ leaves. That is
  $$
  v(x) = \frac{d}{dt} \Big|_{t=0} (g^tx)
  $$
  The phase velocity vectors of all points form a [[Real Analysis|smooth]] [[Vector Field|vector field]] called the **phase velocity field**.
	* The fixed points of the flow are [[Integral Curve|equilibrium points]] of the phase velocity field. Conversely, the equilibrium points of the phase velocity field are precisely the fixed points of the flow. 
	* (*Arnold 4.4.1*) Consider the mapping $\varphi: R\to M$ 
	  $$
	  \varphi(t) = g^tx_0
	  $$
	  This mapping is a solution to the equation 
	  $$
	  \dot x = v(x) 
	  $$
	  With initial condition $\varphi(0)=x_0$.
	* Under the action of the phase flow, *the phase point moves so that its velocity vector at any instant equals the phase velocity vector at the point of the phase space at which the moving point is located*.

* The **phase flow** of the differential equation $\dot x = v(x)$ is the one-parameter diffeomorphism group for which $v$ is the phase velocity vector field.
  
  To find the phase flow, it suffices to solve $\varphi(t) = g^tx_0$ with initial condition $\varphi(0)=x_0$.
	* *Not every smooth vector field is a phase velocity vector field of a flow.* In particular, we require the smooth vector field to be defined on a [[Real Analysis|compact vector space]].
	* Every smooth vector field $v$ on the line that has at most linear growth at infinity (i.e., $|v(x)| \le a + b|x|$) is the phase velocity field of a one-parameter group of diffeomorphisms on the line
		* *Proof*: It can be verified that $\dot v(x) \le b + 1$. Thus, it is bound and is continuous on the entire $t$-axis. 


# Links
* [[Ordinary Differential Equations by Arnold]]
* [[Differential Calculus]]