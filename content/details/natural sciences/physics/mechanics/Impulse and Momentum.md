* The **linear momentum** of a particle, denoted $\vec{p}$ is defined as 
  
  $$
  \vec{p} = m\vec{v}
  $$
  *Momentum quantifies motion*.

* The **impulse** of an external force us defined as the product of the net external force and the time interval
  
  $$
  \vec{J} = \vec F_\text{net} \ \cdot \Delta t
  $$
  For a varying force, we have that 
  
  $$
  \vec{J} = \int \vec{F} (t) \ dt
  $$


* The **Impulse Momentum Theorem** states that the impulse of a force on a particle during a time interval equals the change in momentum during that interval
  
  $$
  \vec{J} = \Delta \vec{p}
  $$
  This follows from [[Newtonian Mechanics|Newton's Second Law]]. 

	* A small force acting for a long time has the same effect on an object's motion as a larger force acting for a short time because impulse is the same regardless. 
	* This is different from the [[Work and Energy|Work-Energy Theorem]] work depends on distance, whereas impulse depends on time.
	* The sum of the external forces on the system equals the rate of change of the total momentum of all particles in the system. This follows because of the Conservation of Momentum and the additivity of forces
	  
	  $$
	  \begin{split}
	  \vec{F}_\text{net} &= \vec{F}_\text{int} + \vec{F}_\text{ext}
	  \\ 
	  \vec{F}_\text{net} &= \frac{d\vec{p}_\text{net}}{dt} + \vec{F}_\text{ext}
	  \end{split}
	  $$


* **Law of Conservation of Momentum** In a closed system where matter is not exchanged and where external forces do not act, the total momentum remains constant. That is if we have particles numbered $1,\dots, n$
  
  $$
\sum_{i=1}^n \vec{p}_i = k
  $$
  Where $k$ is some constant.
  
  This follows from [[Newtonian Mechanics|Newton's Third Law]]
  
  This holds more generally than the Conservation of Total Mechanical Energy (i.e., for non-conservative forces)
	* A more general explanation has to do with the fact that for an inertial [[Kinematics|frame of reference]], motion looks the same. A [[Group Theory|symmetry argument]] can then be formulated as the universe is symmetric across space in the sense that *the laws of physics apply regardless of where we are in space*

* *Unlike, Energy which can be concealed in more subtle forms like heat and mass, momentum (in a mechanical system) cannot be hidden*. If there is a non-zero momentum, then the object must be moving and that motion is observable.
	* [Momentum in an electromagnetic field between two particles at a large distance apart will, for a brief moment, not appear to be conserved when simply observing their motions. The momentum is "hidden" in the electromagnetic field](https://www.feynmanlectures.caltech.edu/I_10.html)
# Collisions
* A **collision** is any strong interaction between objects that lasts a relatively short time
* *By the Law of Conservation of Momentum, the total momentum of the colliding objects is the same value before and after the collision, assuming no external forces.*
* A collision is **elastic** if the forces involved in the collision are conservative.  A collision is **inelastic** if there are non-conservative forces at place. A collision is **completely inelastic** if after the collision the two objects are stuck together and move as one.

* Another way to quantify a collision's elasticity is to look at the kinetic energy before and after the collision. For this, we denote $i$ and $f$ for before and after respectively.
	* Elastic means that $\text{KE}_i = \text{KE}_f$
	* Inelastic means that $\text{KE}_i > \text{KE}_f$.
	* Perfectly inelastic means that the maximum amount of kinetic energy was lost. The velocity of the two objects are the same by the end. 

* In an elastic collision, the [[Kinematics|relative velocities]] before and after the collision have the same magnitude but opposite signs.    That is
  $$
  \vec{v}_{Bf} - \vec{v}_{Af} = -(\vec{v}_{Bi} - \vec{v}_{Ai})  
  $$
	* If the masses of the two objects are the same, then one object will stop and transfer its momentum to the other object. In general, *the object with lower mass transfers some of its kinetic energy to the object with higher mass.*

* In a system of particles where $\vec{v}_\text{CM}$  is the velocity of the center of mass in this system, $M$ is the total mass of the system, and $\vec{p}_\text{tot}$ is the total momentum of the system, we have
  
  $$
  \vec{p}_\text{tot} = M\vec{v}_\text{cm}
  $$
  Essentially *the motion of an object can be described using its center of mass*. 
	* If there is no external force on a system, the center of mass maintains the same velocity.
	* If there is an external force, the center of mass moves as though all mass was concentrated at that point so that
	  $$
	  \sum \vec{F}_\text{ext} = M\vec{a}_\text{cm}
	  $$
	* If the total mass of the system is constant, we have
	  $$
	  \sum \vec{F}_\text{ext} = \frac{d\vec{p}_\text{tot}}{dt}
	  $$

* Between very elementary objects (i.e., where there is no clear separation between them or when collisions leave them unchanged), the collisions are always elastic or very nearly elastic

# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] - Ch. 8
