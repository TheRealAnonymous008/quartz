* Rigid Body Simulation builds off of the dynamics of [[Kinematics|Particles]]. 
* Each particle has an associated position and velocity [^phase_space] . The entire system has a state
  $$
  X(t) = \begin{bmatrix}
  x_1(t) & v_1(t) \\ 
  \vdots & \vdots \\ 
  x_n(t) & v_n(t) 
  \end{bmatrix}
  $$
  The dynamics follow that of [[Newtonian Mechanics|Newton]] (see the [[Ordinary Differential Equation|ODE]] below)
  $$
  \dot X(t) = \begin{bmatrix}
  v(t) \\ 
  F(t) / m
  \end{bmatrix}
  $$
  With initial conditions $x(0)$ and $v(0)$. 

[^phase_space]: We may also interpret this as each particle's state being a phase in a phase space (in the [[Physics]] sense where mass is $1$, not the Differential Equations sense)


* We assume that we [[Numerical Differential Equations|numerically solve our differential equations]].

# From Particles to Rigid Bodies
## Theory
* Rigid Bodies are characterized with both a translation $x(t)$ and a rotation $R(t)$ .
* Rigid Bodies are not scaled. Therefore, we define a fixed space called the **Body Space**. $R(t)$ and $x(t)$ transform the body space to world space. 
* *Assume*: The [[Mass|Center of Mass]] is at the origin. 
	* $x(t)$ can be interpreted the location of the center of mass at time $t$ (see below). This can be proven mathematically.
	* $R(t)$ can be interpreted as the position of the axes in body space at time $t$. 

* Every point $p_0$ on the rigid space (in Body Space) is transformed as follows:
  $$
  p(t) = R(t) p_0 + x(t) 
  $$

* Linear velocity is defined as 
  $$
  v(t) = \dot {x} (t) 
  $$

* If we have a rotation matrix, then we can define the angular velocity as follows
  $$
  \dot R(t) = \omega (t) \ast R(t)
  $$
  Where
  $$
  a \ast b = \begin{bmatrix}
  0 & -a_z & a_y \\ 
  a_z & 0 & -a_x \\ 
  -a_y & a_x & 0
  \end{bmatrix} = a\times b
  $$
  And we apply this column wise so that
  $$
  \omega (t) \ast R(t) = \begin{bmatrix}
  \omega (t) \ast R_1(t)  & \omega(t) \ast R_2(t) & \omega (t) \ast R_3(t)
  \end{bmatrix}
  $$

* To calculate mass, we *conceptually assume that the rigid body is composed of $N$ particles*. Let $r_{0i}$ denote  the location of the particle in rigid body space.  The dynamics of this particle are the same as that of the rigid body
  $$
  r_i(t) = R(t) r_0 + x(t) 
  $$
  The total mass $M$ is simply the sum of all individual particle masses $m_i$
  $$
  M = \sum_{i} m_i 
  $$
	* The velocity of a particle can be calculated using its dynamics [^particle_vel]
	  $$
	  \begin{split}
	  \dot r(t) &= \omega (t) \ast R(t) r_{0i} + v(t) \\
	  &= \omega(t) \ast (R(t) r_{0i} + x(t) - x(t)) + v(t) \\ 
	  &= \omega(t) \ast (r_i(t) - x(t)) + v(t) \\
	  &= \omega(t) \times (r_i(t) - x(t) ) + v(t) 
	  
	  \end{split}
	  $$
	* The center of mass of the system is defined as
	  $$
	  \frac{1}{M}\sum_i m_ir_i (t)  
	  $$
	  The body coordinate system is defined so that
	  $$
	  \frac 1 M\sum_{i} m_ir_i = \begin{bmatrix}
	  0 \\ 0 \\ 0 
	  \end{bmatrix}
	  $$
	* One important relation is as follows
	  $$
	  \sum_i m_i (r(t) - x(t))  = \sum_i m_i (R(t) r_{0i} + x(t) - x(t)) = R(t) \sum_{i} m_i r_{0i} = \vec{0}
	  $$
	  Intuitively this says that the first moment of mass is $\vec{0}$.



[^particle_vel]: Intuitively, the movement of the particle is defined as first rotating about the center of mass, then translating in world space. The former is done by considering its position in world space $r_i(t)-x(t)$. The latter is done by following the velocity of the rigid body. 

* To introduce dynamics, we assume that at a geometric location of interest on the rigid body, there is a particle. Let $F_i(t)$ be the total force from external forces on particle $i$. Also let $\tau_i(t)$ be the external torque.
  
  The torque is defined as 
  $$
  \tau_i(t)  = (r_i(t) - x(t) ) \times F_i(t)
  $$
* The total force and total torque is defined as [^summation]
  $$
  \begin{split}
  F(t) &= \sum_i F_i (t) \\
  \tau (t) &= \sum_i \tau_i (t)  
  \end{split}
  $$
	* *The torque tells us the distribution of forces on the body*.

[^summation]: Notice that all summation formulas of this form are really [[Numerical Integral Calculus|discretized methods for doing integrals]].

* The [[Impulse and Momentum|momentum]] of the system is defined as the total momentum of our particles
  $$
  \begin{split}
  P(t) &= \sum_i p_i \\ 
  &= \sum_{i}m_i\dot r_i(t) \\ 
  &= \sum_i m_i v(t) + \omega(t) \times \sum_{i} m_i (r_i(t) -x(t)) \\ 
  &= \sum_{i}m_iv(t) \\ 
  &= Mv(t) 
  \end{split}
  $$
	* Thus, the linear momentum and the force are related as follows
	  $$
	  F(t) = \dot P(t) 
	  $$
* The angular momentum of the body is defined ass
  $$
  L(t) = I(t) \omega(t) 
  $$
  Where $I(t)$ is the inertia tensor. The Torque and the Angular Momentum are related as follows: 
  $$
  \dot L(t) = \tau (t) 
  $$

* As a sanity check, we have that *linear momentum is not dependent on the body's rotation and angular momentum is not dependent on the body's translation*.

* The Inertia Tensor $I(t)$ is defined as follows. Let $r_i'=r_i(t)-x(t)$ be the displacement of the $i$-th particle from the center of mass, then $I(t)$ is defined using the  following
  $$
  I_i(t) = \sum_i \begin{bmatrix}
  m_i(r_{iy}'^2 + r_{iz}'^2) & -m_ir_{ix}'r_{iy}' & -m_ir'_{ix}r'_{iz}\\
  -m_ir_{iy}'r_{ix}' & m_i(r_{ix}'^2 + r_{iz}'^2) & -m_i r_{iy}' r_{iz}' \\
  -m_ir_{iz}'r_{ix}' & -m_i r_{iz}' r_{iy}' & m_i(r_{ix}'^2 + r_{iy}'^2)
  \end{bmatrix}
  $$
	* Another way to write this is as follows. Denote $\mathbb{1}$ as the Identity Matrix.  Then
	  $$
	  \begin{split}
	  I(t) &= \sum_i m_i (\ (r_i'^T  r_i') \mathbb{1} -r_i' r_i'^T \ ) \\
	  &=   \sum_i m_i (\ (R(t) r_{0i})^T (R(t)r_{0i}) \mathbb{1}  - (R(t) r_{0i}) (R(t) r_{0i})^T\ ) \\ 
	  &=  \sum_i m_i (r_{0i}^T R(t)^T R(t) r_{0i} \mathbb{1}  - R(t) r_{0i}r_{0i}^T R(t)^T) \\
	  &= \sum_{i} m_i ((r_{0i}^T r_{0i})\mathbb{1} - R(t)r_{0i} r_{0i}^T R(t)^T) \\ 
	  &= R(t) \left(\sum_i m _i ((r_{0i}^T r_{0i} ) \mathbb{1} - r_{0i} r_{0i}^T)\right) R(t)^T
	  \end{split}
	  $$
	  Note that $R(t)$ is an [[Unitary and Orthogonal Operators|orthogonal]] matrix so that $R^T(t) R(t) = \mathbb{1}$.  We also treat $r_{0i}^T r_{0i}$ as a scalar.
	* Now define the mass of the body as 
	  $$
	  I_{\text{body}} = \sum_i m _i ((r_{0i}^T r_{0i} ) \mathbb{1} - r_{0i} r_{0i}^T)
	  $$
	  The Inertial Tensor is then 
	  $$
	  I(t) = R(t) \  I_{\text{body}} \ R(t) ^T
	  $$

## Implementation Considerations
* The state of the rigid body $X(t)$ is now defined as
  $$
  X(t) = 
  \begin{bmatrix}
  x(t) \\ R(t)  \\ P(t) \\ L(t) 
  \end{bmatrix}
  $$
  We assume that $M$ and $I_{\text{body}}$ are constants.
  
  We also compute
  $$
  \begin{split}
  v(t) &= \frac{P(t)}{M} \\
  I(t) &= R(t) I_{\text{body}} R(t)^T \\
  \omega(t) &= I(t)^{-1} L(t )
  \end{split}
  $$
  To calculate the derivative
  $$
  \frac{d}{dt}X(t) =  \begin{bmatrix}
  v(t) \\ 
  \omega (t) \ast R(t) \\
  F(t) \\
  \tau (t)
  \end{bmatrix}
  $$

* The rotation transformation $R(t)$ can be represented either as a [[Matrix|matrix]] or as a [[Complex Numbers and Quaternions|Quaternion]]. 
* The *Quaternion Approach is better since it is less susceptible to drift when numerically computed.*
	* We represent the quaternion $s+v_x\hat i + v_y\hat j + v_z \hat k$ as $[s,v]$. 
	* Each quaternion is assumed to be a unit quaternion.
	* Rotation of $\theta$ radians about a unit axis $\hat u$ is then represented as 
	  $$
	  [cos(\theta / 2), \sin (\theta / 2) \hat u ]
	  $$
	* The product $\cdot$ of the quaternions indicate composite rotation. 
	* Angular velocity is defined using
	  $$
	  \dot q(t) = \frac 1 2 [0, \omega(t)] \cdot q(t) 
	  $$
	* The Rotation Matrix is then derived from the quaternion $q(t)$ when we need it.
# Contact and Collision



# Links
* [^baraff_1997]  - Primary Source and Seminal Paper.

[^Baraff_1997]: Barach (1997). [An Introduction to Physically Based Modeling: Rigid Body Simulation I—Unconstrained Rigid Body Dynamics](https://www.cs.cmu.edu/~baraff/sigcourse/notesd1.pdf)