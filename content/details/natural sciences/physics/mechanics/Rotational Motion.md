* We say that an axis of rotation is a **[[Group Theory|symmetry]] axis** if the object can be rotated along this axis such that the positions before and after the rotation are indistinguishable. 
# Tangential [[Kinematics]]
* A point mass moves in **uniform circular motion** if it moves in a circle at constant speed. 
	* In this scenario, there is no change of acceleration parallel to the path. Thus, *acceleration is perpendicular to the path and directed inward*.
	* Let ${a}_\text{rad}$ be the magnitude of acceleration of an object in uniform circular motion. If the object travels in radius $R$ and speed $v$, we have
	  
	  $$
	  {a}_\text{rad} = \frac{v^2}{R}
	  $$

	* Let $T$ be the period of motion. The speed is given as 
	  
	  $$
	  v = \frac{2\pi R}{T}
	  $$

* When we have non-uniform circular motion, a component of acceleration is tangent to the instantaneous velocity. This vector is given by $\vec{a}_\text{tan}$ and is defined as
  
  $$
  \vec{a}_\text{tan} = \frac{d\vec{v}}{dt}
  $$
  The component perpendicular to the motion is still given by $\vec{a}_\text{rad}$ above. 

* Objects in circular motion experience [[Kinds of Forces|Centripetal force]].

# Orbit Kinematics
* For the following, we assume that any bodies are idealized rigid bodies
* The **angular coordinate** $\theta$ is the angle between the object and an axis of rotation. We assume that the axis of rotation is fixed with respect to an [[Newtonian Mechanics|inertial frame of reference]]
* The **angular velocity** is defined as 
  $$
  \vec{\omega}= \frac{d\theta}{dt}
  $$
	* At any instant, every part of a rotating rigid body has the same angular velocity. This is because all parts of the system must travel the same angle.
	* The angular velocity vector is directed along the axis of rotation, perpendicular to the plane of rotation following the right hand rule.
	* The tangential velocity is related to the angular velocity as follows
	  $$
	  \vec{v} = \vec{\omega} \times \vec{r}
	  $$
	  Where $\times$ represents the cross product and $\vec{r}$ is the position vector relative to the axis of rotation.
	* The tangential speed is related to the angular speed by
	  $$
	  v = \omega \cdot r
	  $$
	  
* The **angular acceleration** is defined as 
  $$
  \vec\alpha = \frac{d\omega}{dt}
  $$
	* The angular acceleration is related to the tangential acceleration as follows
	  $$
	  \vec{a} = \vec{\alpha} \times \vec{r}
	  $$
	  Where $\times$ represents the cross product and $\vec{r}$ is the position vector relative to the axis of rotation.
	* The magnitudes of the angular and tangential acceleration is related by
	  $$
	  a = \alpha \cdot r
	  $$
	* The centripetal component of the acceleration can then be derived as
	  $$
	  a_\text{rad} = \omega^2 r
	  $$

	* When the angular acceleration is constant, the [[Kinematics|kinematic equations]] still hold except with $\theta, \omega, \alpha$ instead of $s, v,a$ respectively. 

# Rotational Dynamics
* The mass analogue in this case is the **[[Mass#Moment of Inertia|moment of inertia]]**. 
	* The more particles are far away from the axis of rotation, the higher the moment of inertia.
	* The **rotational [[Work and Energy|kinetic energy]]** of the rigid body is given by
	  $$
	  \text{KE} = \frac{1}{2} I\omega^2 
	  $$
	* The greater the moment of inertia, the greater the kinetic energy of the rigid body rotating.
	* A higher rotational inertia means that it is more difficult to change the system's angular acceleration (analogous to [[Newtonian Mechanics|regular inertia]]).

* *If the rotation axis of a rigid body is not a symmetry axis, $\vec{L}$ does not lie along the rotation axis.* A net torque would be required to maintain rotation

## Torque
* Let $\vec{F}$ be a force. The **torque / moment** of the force applied to a rotating body is defined as 
  $$
  \vec{\tau} = \vec{F} \times \vec{r}
  $$
  Where $\vec{r}$ is the position vector of the force along the **moment arm** defined with respect to a point $O$ from which torque is being measured
  
  If $\vec{F}_\perp$ is the component of the force perpendicular to $\vec{r}$ following the right hand rule, then 
  $$
  \tau = \vec{F}_\perp \ r
  $$
	* *Torque is the rotational analogue of Force*. 
	* *Notation*: By convention, we assume that unless otherwise stated, the torque is measured from the same axis as the angular displacement, velocity and acceleration

* **Varignon's Theorem** states that the net torque is also the sum of the individual torques due to each force. That is 
  $$
  \tau_\text{net} = \sum_{i} \vec{r}_i\times \vec{F}_i 
  $$


* A rotational analogue of [[Newtonian Mechanics|Newton's Second Law]] states that
  $$
  \vec\tau_{\text{net}} = I\vec\alpha
  $$
  Where the angular acceleration and torque are relative to the same axis.
  
  Note *this only applies for rigid bodies where angular acceleration is the same for all parts of the system*.
	* The torque on each particle is due to the net force on that particle. 
	* The torques for each pair of particle are equal and opposite because of Newton's third law.
	* *All internal torques sum to $0$* so the rotational analogue gives the sum of the external torques.
	* This applies even for a moving axis of rotation as long as.
		* The axis through the center of mass is an axis of symmetry.
		* The axis must not change direction,

* An object's **center of gravity** is the point on a body where the torque due to gravity vanishes.
	* The torque due to gravity is given by
	  $$
	  \vec{T} = \vec{r}_\text{cm} \times \vec{w}
	  $$
	* If $\vec{g}$ has the same value at all points on an object, the center of gravity is identical to the center of mass.
	* *In general, however, the center of gravity need not be at the center of mass*
	* In most cases near the earth's surface, we can approximate that the center of gravity equals the center of mass.
	* An object in rotational [[Mechanical Equilibrium|equilibrium]] and acted on by gravity supported by a single point $P$ has a center of gravity along an axis that passes through $P$ extending in the direction of gravity.
	* An object with multiple supports will have its center of gravity somewhere within the area bounded by the supports
		* *The lower the center of gravity and the larger the area of support, the harder to overturn an object*
## Work and Energy
* For a system that is both moving and rotating, the kinetic energy is given as the sum of the kinetic energy using the linear and rotational formulae for kinetic energy.
  
  We use a moment of inertia running through the center of mass
  
  $$
  K_\text{net} = \frac{1}{2} M v_{\text{cm}}^2  ++ \frac{1}{2} I_\text{cm} \omega^2 
  $$
	* *Intuition*: The additive relationship derives from the velocity having a translational and rotational component which can be separated. Remember to treat $v^2=\vec{v} \cdot \vec{v}$
	* *In order for an object to **roll without slipping**, the point on the object that contacts the surface must instantaneously be at rest so that it does not slip*. This is achieved when 
	  $$
	  v_\text{cm} = R\omega
	  $$
	  Where $R$ is the radius of the wheel.
		* For a rigid body that rolls without slipping, the kinetic energy of rotation depends on the shape of the rigid body.


* The [[Work and Energy|Work]] done by a torque is given using the following integral
  $$
  W = \int_{\theta_1}^{\theta_2} \tau  \ d\theta 
  $$
  Where torque and angular displacement is measured in the same direction for rotation about a fixed axis through the  center of mass. 
	* The Work-Energy theorem still applies 
	* Power can also be derived similarly by using
	  $$
	  P = \tau \cdot \omega 
	  $$

## Momentum
* The **angular momentum** is the analogue for [[Impulse and Momentum|momentum]]. Assuming it is taken relative to the origin $O$. It is defined as follows for situations when the axis of rotation is a symmetry axis
  $$
  \vec{L} = I\vec{\omega}
  $$

* It is related to linear momentum by
  $$
  \vec{L} =\vec{r} \times \vec{p} 
  $$
  Where $\vec{r}$ is the position relative to $O$ and assuming we are in an inertial frame of reference.

* The angular momentum is related to the torque in a similar manner as linear momentum and force
  $$
  \tau_\text{net} = \frac{d\vec{L}}{dt}
  $$

* **Law of Conservation of Angular Momentum**. When the net external torque acting on a system is $0$, the total angular momentum of the system is constant. That is for a system with $n$ particles
  
  $$
  \sum_{i=1}^n \vec{L} = k
  $$
  Where $k$ is some constant.
	* As with collisions, internal forces can transfer angular momentum but can't change the total angular momentum of the system.

# Precession
* A **precession** is the movement of the axis around another axis due to torque acting to change the direction of the first axis.
* Precession is simply the rotational analog of uniform circular motion (assuming it is torque-free). The angular velocity changes orientation with time which induces a varying moment of inertia.
	* In this case, the velocity of each axis varies inversely to the axis' moment of inertia. 

# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]]  - Ch. 9 - 10