* **Dynamics** is concerned with the causes of motion. The primary objects of study are **forces** -- any interaction between two objects. 

* Forces are typically described as a push or a pull.
	* **Contact Forces** involve direct contact between two objects.
	* **Normal Force** is exerted between an object and the surface that it is on. *It is always perpendicular to the surface of contact*. [^normal_force]
	* **Friction** is exerted *parallel to the surface* in the direction that opposes the motion of the object.
	* **Tension** is a pulling or stretching force transmitted along an axis. [^tension]
	* **Compression** is the opposite of tension which acts as a force that pushes inwards
	* **Weight** is the force exerted by gravity. 

[^normal_force]: The normal force is not necessarily equal to weight. For example, when an object is in an incline, the normal force is less than the weight. This is what causes an object to slide down a slope. 

[^tension]: Tension is not necessarily equal to weight.

* *Forces are vectors* and they can be superimposed on top of each other to get the net force. That is 
  
  $$
  \vec{F}_\text{net} = \sum \vec{F}
  $$

* The laws governing forces are valid under an inertial frame of reference. In a non-inertial frame of reference, we typically see **pseudo-forces** which require us to adjust for some form of translation or rotation over time.
	* Einstein's hypothesis was that pseudo-forces cannot be distinguished from gravity since gravity has a spatial component to it, and we may simply be analyzing it with the wrong coordinate system.
## Basic Examples

* *The apparent weight of an object is the normal force*. The actual weight is the one calculated using mass and gravity. 
	* These two need not be the same as in the case of apparent weightlessness. In fact, we can explain this as a normal force felt when accelerating at $\vec{a}=-g$

* The **Centripetal Force** is applied to objects in [[Rotational Motion|rotation]]. It can be calculated with the following formula
  $$
  F_\text{net} = \frac{mv^2}{R}
  $$
	* Here the *force is directed inside*. This allows the object to maintain its circular trajectory.  [^centrifugal]
	* Centripetal Force can come from any source (normal force, friction, etc)

[^centrifugal]: *Centrifugal Force is different from centripetal force*. It is the force going outwards and would cause the object to move in a straight line. *In an inertial frame of reference, there is no such thing as centrifugal force*.

* **Hooke's Law** states that for an ideal spring, the force needed to compress or stretch the spring follows
  
  $$
  F = k{x}
  $$
  Where $k$ is the spring constant and $\vec{x}$ is small compared to the deformation of the spring. $x>0$ means the spring was stretched.  
  
  A general form of Hooke's Law is seen [[Continuum Mechanics|here]].
## Friction
* *Friction is always perpendicular to the normal force by definition*
* Friction occurs between two surfaces because atoms are bonding and unbonding, exerting a small amount of resistance on the object.
* Keep in mind that all coefficients of friction are approximations calculated from experiments. 

* **Static friction force** acts between surfaces that are not moving relative to each other.
	* It is proportional to the normal force. It is harder to move a heavier object. We refer to the proportionality constant $\mu_s$ as the **coefficient of static friction**
	  $$
	  {F}_s \le \vec{F}_{s\text{max}}= \mu_s \cdot {F}_n
	  $$
	* Motion only happens when we are able to counteract static friction. That is, when ${F}_a = \mu_s {F}_n$.
	* If $F_a < \mu_s {F}_n$, the static friction is stronger and the object does not move. 
	* The magnitude of static friction equals the applied force assuming it is less than the maximum static friction (see [[Newtonian Mechanics#Newton's Laws|Newton's Laws]]). 
	  
	  $$
	  {F}_s ={F}_a \ \ \ \ \text{if } {F}_a \le {F}_{s\text{max}}
	  $$
* The **kinetic friction force** is one that acts between moving surfaces.[^friction_1]
	* The magnitude is usually proportional to the normal force. It is harder to stop a heavier object in motion. We refer to the proportionality constant $\mu_k$ as the **coefficient of kinetic friction
	  
	  $$
	  F_k  =\mu_k \cdot  {F}_n
	  $$
	* Kinetic friction is usually not constant.
	* *It is the same whether or not the object is accelerating* since it only depends on the normal force. 
* *Sometimes an object might stick and un-stick to the surface*. In this case, static and kinetic friction alternate. 

[^friction_1]: In the case of sliding objects, the friction is due to [[Chemistry|chemical bonds]] forming between the two surfaces.

* **Rolling Friction** is defined as the friction resisting the motion of a rolling body (i.e., a wheel) on a surface. It is defined with the formula
  
  $$
  F_r = \mu_r \cdot F_n
  $$
  Where $\mu_r$ is the **coefficient of rolling friction** also called the **tractive resistance**.


* **Fluid Resistance / Drag** is the frictional force that a fluid exerts on an object moving through the liquid. The force is exerted opposite the object's motion. It is defined using the following formula
  
  $$
  F_D = \frac{1}{2} \rho v^2 \mu_D \ A
  $$
  Where $A$ is the cross sectional area of the object touching the fluid, $\mu_D$ is the **drag coefficient** and $v$ is the speed relative to the fluid.
	* For slow moving particles, we can approximate the above as 
	  $$
	  F_D \approx \frac{1}{2} \rho v \mu_D A
	  $$
	* Drag explains why, on earth, heavy objects fall faster than light objects. In particular, we can calculate the **terminal velocity** of an object in freefall as
	  
	  $$
	  \begin{split}
	  v_t &= \sqrt{\frac{mg}{D}} \\
	  D &= \frac{1}{2}\mu_D A\\
	  \end{split}
	  $$

## Conservative Forces
* A force is said to be **conservative** if it allows for two-way conversion between kinetic and potential energy.
	* When force is conservative work is always reversible.
	* When force is conservative, work is path independent. The work is simply given by 
	  $$
	  W = \Delta \text{PE}
	  $$
	* When the starting and ending point of the object's trajectory are the same, $W=0$.

# Fundamental Forces
* These forces are fundamental in the sense that *their underlying laws are fundamentally simple*
## [[Gravity]]

## Electromagnetic Force
* **Coulomb's Law** states that given two charges $q_1$ and $q_2$, separated a distance $r$, the electromagnetic force between them is given by 
  
  $$
  \vec{F} = \frac{k_e q_1q_2}{r^2}
  $$
  Where $k_e$ is a constant and $q_1, q_2$ are signed depending on whether they are positive or negative.

* Like charges repel each other, while opposite charges attract.
* *Electrostatic forces are stronger than Gravity*.

# Links 
* [[University Physics with Modern Physics 15th Edition By Freedman]]
* [[Kinematics]]