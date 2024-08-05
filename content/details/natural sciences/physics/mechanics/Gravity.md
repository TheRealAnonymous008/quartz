# Kinematics
* In free fall, objects accelerate due to gravity. We denote the acceleration due to gravity as $g$.
	* If a freely falling object passes a given point at two different times, once moving upward and once moving downward, its speed will be the same at both times.
	* When the acceleration of an object is constant, its position as a function of time is given by a quadratic equation.

* The motion of a projectile is a combination of motion with constant velocity in the horizontal $x$-direction and motion with constant downward acceleration in the vertical $y$-direction.
* *Velocity and Acceleration are perpendicular only at the peak of the trajectory*.

# Dynamics
* The **Law of Gravitation** states that every object attracts every other objects with a gravitational force $F$ that follows
  
  $$
  F = \frac{Gm_1m_2}{r^2}
  $$
  Where $G$ is the gravitational constant and $r$ is the distance between the two objects with masses $m_1$ and $m_2$. 
	* If the objects are not point masses, we can approximate by using the [[Mass|center of mass]]. 

* Gravity can be formulated as acting on a **field**. One object emits this field at all points in space, and the force acts on an object at a particular point.


# Orbits
* An object **orbits** around a body if it is falling towards the body constantly in such a way that it maintains a certain distance away from the body.
  
  The speed an object needs to maintain an orbit of radius $r$ around an object with mass $M$ is calculated as
  
  $$
  v= \sqrt{\frac{GM}{r}}
  $$
  
  This derives from the Law of Gravitation and [[Newtonian Mechanics|Newton's Second Law]]. In particular, we take the mass of the object $m$ and the centripetal acceleration $a=\frac{v^2}{r}$. Both forces must balance since the object stays in orbit (i.e., does not decrease in height)
  
  $$
  \frac{GM m}{r^2} = \frac{mv^2}{r}
  $$

* The **Period** $T$ of a circular orbit is related to the speed in that the speed is the distance traveled in one revolution. 
  
  $$
  v = \frac{2\pi r}{T}
  $$
	* The period can also be derived by using the calculation of orbit speed above
	  $$
	  T = \frac{2\pi r^{3/2}}{\sqrt{GM}}
	  $$
	  We can generalize the above for elliptic orbits. Let $a$ be the semi-major axis $a$
	  
	  $$
	   T = \frac{2\pi a^{3/2}}{\sqrt{GM}}
	  $$


* **Kepler's Laws of Planetary Motion** describes the orbits of planets around the sun.
	* **Law 1**: The orbit of a planet is an ellipse with the Sun as one of the two foci.
	* **Law 2**: A line segment joining a planet and the Sun sweeps out equal areas during equal intervals of time. The **sector velocity** is the velocity of this sweeping line. It is calculated as 
	  $$
	  \frac{dA}{dt} = \frac{1}{2}r^2 \frac{d\theta}{dt}
	  $$
	  Kepler's Second Law states that *sector velocity is constant*. 
	* **Law 3**: The square of the period of the orbit is proportional to the cube of the length of the semi-major axis of the orbit.
* *The laws of planetary motion are a consequence of the Laws of Universal Gravitation*
	* For an object acted on by an attractive force proportional to $1/r^2$, the only possible closed orbits are a circle or an ellipse. A generalization of this is that all orbits are conic sections (open trajectories are hyperbolic or parabolic).
	* The second law follows from the conservation of [[Rotational Motion|angular momentum]].
	* The third law follows from  the calculation above on the orbit's period.
# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] - Ch. 13