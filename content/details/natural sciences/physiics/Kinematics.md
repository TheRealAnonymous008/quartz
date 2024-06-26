* **Kinematics** gives us the tools to describe motion. 

* Consider a point mass, the **displacement** of the point mass is the [[Linear Algebra|vector]] which points from its starting point $x_i$ to its ending point $x_i$. We denote the displacement as $\vec{s} = \Delta x = x_f - x_i$.
* Displacement can be a function of time $s(t)$. Viewed in this way, the **velocity** is defined as 
  
  $$
  \vec{v}(t) = \frac{d\vec{s}}{dt}
  $$
  And **acceleration** is defined as 
  $$
  \vec{a}(t) = \frac{d\vec{v}}{dt}
  $$
  Discrete variants of these also exist where we replace the differentials with approximations (i.e. $dx = \Delta x$).

* *The velocity is tangent to the point mass' trajectory at every point.*
* **Speed** is defined as the magnitude of velocity. **Distance** is defined as the magnitude of displacement.

* From the above definitions, we can define the four **Kinematic Equations**
  
  $$
  \begin{split}
  s &= v_i t + \frac{1}{2}at^2 \\ 
  v_f^2 &= v_i^2 + 2as \\
  v_f &= v_i + at \\
  s &= \frac{v_f+v_i}{2} t
  \end{split}
  $$

* Acceleration can be redefined using bases that are parallel and perpendicular along its path of motion. *This translates into a change in speed and turning, respectively*.
	* If a moving object is turning (changing direction),its acceleration vector points ahead of the normal to its path if it is speeding up
	* Its acceleration points behind the normal if it is slowing down
	* Its acceleration points along the normal if its speed is instantaneously not changing.
\
# Gravity
* In free fall, objects accelerate due to gravity. We denote the acceleration due to gravity as $g$.
	* If a freely falling object passes a given point at two different times, once moving upward and once moving downward, its speed will be the same at both times.
	* When the acceleration of an object is constant, its position as a function of time is given by a quadratic equation.

* The motion of a projectile is a combination of motion with constant velocity in the horizontal $x$-direction and motion with constant downward acceleration in the vertical $y$-direction.
* *Velocity and Acceleration are perpendicular only at the peak of thee trajectory*.

# Circular Motion
* A point mass moves in **uniform circular motion** if it moves in a circle at constant speed. 
	* In this scenario, there is no change of acceleration parallel to the path. Thus, *acceleration is perpendicular to the path and directed inward*.
	* Let $\vec{a}_\text{rad}$ be the magnitude of acceleration of an object in uniform circular motion. If the object travels in radius $R$ and speed $v$, we have
	  
	  $$
	  \vec{a}_\text{rad} = \frac{v^2}{R}
	  $$

	* Let $T$ be the period of motion. The speed is given as 
	  
	  $$
	  v = \frac{2\pi R}{T}
	  $$

* When we have non-uniform circular motion, a component of acceleration is tangent to the instantaneous velocity. This vector is given by $\vec{a}_\text{tan}$ and is defined as
  
  $$
  \vec{a}_\text{tan} = \frac{d|\vec{v}|}{dt}
  $$
  The component perpendicular to the motion is still given by $\vec{a}_\text{rad}$ above. 

# Relativity
* **Relativity** is the phenomenon where two observers measure the velocity of the same object differently if one observer is moving relative to the other. **Relative velocity** is the velocity relative to a particular observer.
* Every observer is assumed to have a **frame of reference** - a coordinate system plus a time scale.

* The velocity of object $P$ relative to $B$ is denoted as $\vec{v}_{P/B}$. If we have another observer $A$, then we have that 
  
  $$
  \vec{v}_{P/A} = \vec{v}_{P/B} + \vec{v}_{B/A}
  $$
* For two objects, the relative velocity is given by 
  $$
  \vec{v}_{A/B} = \vec{v}_A - \vec{v}_B
  $$
* All of the above extends to any other quantity (i.e., position or acceleration)

# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] 
* [[Calculus]]