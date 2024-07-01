* The **Work** done by a force is defined as the energy transferred by that force on an object along a displacement. More formally for a constant force we have
  
  $$
  W = \vec{F} \cdot \vec{s}
  $$
	* The work is, effectively, a measure of how similar the direction of the force is compared to the object's displacement.
* In the general form, when force is not constant The total work is given using the following [[Integral Calculus|line integral]]. Denote the path taken as $C$.
  $$
  W =\int_C \vec{F} \cdot d\vec{s}
  $$



* The **Kinetic Energy** of an object is the energy it possesses due to its motion. It is defined as follows
  
  $$
  \text{KE} = \frac{1}{2}mv^2
  $$
* The **Work Energy Theorem** states that the total work done is equal to the change in Kinetic Energy. That is
  
  $$
  W_\text{net} = \Delta \text{KE}
  $$
  *Proof (Average Case)*: Using [[Newtonian Mechanics|Newton]]'s Second Law and the definition of Work. 
	* Viewed in this way, the kinetic energy equals the amount of work you must do to induce to accelerate the object from rest to speed  $v$.
	* *The total kinetic energy can still change even when there is no work being done by anything outside the system*
	* *Proof (Integral Case)*: Observe that $v^2=\vec{v}\cdot \vec{v}$.  We then get the following using the definition of kinetic energy and work
	  
	  $$
	  \frac{d}{dt} \left(\frac{1}{2} mv^2\right) = (m\vec{a}) \cdot \vec{v} = \vec{F}_\text{net} \cdot \vec{v}
	  $$
	  The theorem follows from using the fundamental theorem of calculus and setting $\vec{v} dt = d\vec{s}$
	  This is different from the [[Impulse and Momentum|Impulse-Momentum Theorem]]: work depends on distance, whereas impulse depends on time.

* **Power** is the time rate at which work is done. That is, 
  $$
  P = \frac{dW}{dt}
  $$
	* Using the definition of power and work, we can also derive 
	  $$
	  P = \vec{F} \cdot \vec{v}
	  $$



* The **Potential Energy** is the energy held by an object because of work done on by *a force that is path independent* [^potential_energy]
	* Because of path independence, the formulae for the potential energy of an object due to a force applies regardless of what path the object took.
	* **Gravitational Potential Energy** involves gravity acting on an object near the Earth's surface. It is given by 
	  
	  $$
	  \text{PE}_g = mgy + \text{constant}
	  $$

		* Another way to write this is with the centner of mass $M$
		  $$
		  \text{PE}_g = Mgy + \text{constant}
		  $$
	* **Elastic Potential Energy** involves the force of a spring that has been compressed or stretched with displacement $x$. For an ideal spring, it is given by 
	  
	  $$
	  \text{PE}_\text{el} = \frac{1}{2}kx^2 + \text{constant}
	  $$
	  Here $x>0$ if the string is stretched and $x < 0$ if compressed. $k$ is the force constant of the spring.

* For a given potential function $U(x)$ dependent on position ,the force can be calculated as [^potential_functions]
  
  $$
  F(x)=  -\nabla_x U
  $$
	* Any minimum in the potential function is a stable equilibrium
	* Any maximum in the potential function is an unstable equilibrium. 

* *The work done by all forces other than any conservative force equals the change in total mechanical energy* $E=\text{PE} +\text{KE}$ of the system
  
  $$
  W = \Delta E
  $$
	* When the only forces that act on the object are conservative, the total mechanical energy is constant. 

* The **Internal Energy** of a system is the energy contained within it. It is the amount of energy needed to bring the system from its standard state to its current state.  We denote this with $U_\text{int}$

* The **Law of Conservation of Energy** states that *energy is never created nor destroyed, only transformed*. That is
  $$
  \Delta \text{KE} + \Delta\text{PE} + \Delta U_\text{int} = 0
  $$




[^potential_energy]: See [[Integral Calculus]]. This is connected to the concept of conservative gradient fields and [[Differential Calculus|potential functions]].
[^potential_functions]: The potential function in calculus does not have a negative sign. Here, however, we want the negative sign since we interpret conservative forces as pushing the system towards lower potential energy.

# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] - Ch. 6, 7
* [[Kinds of Forces]]