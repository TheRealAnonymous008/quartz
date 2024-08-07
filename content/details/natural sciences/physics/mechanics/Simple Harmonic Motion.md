* [[Continuum Mechanics|Hooke's Law]] expresses the dynamics of simple harmonic motion where the restoring force is directly proportional to the displacement from equilibrium. 
  
  A harmonic oscillator's acceleration is given as follows
  $$
  a = -\frac{k}{m}x
  $$
  Where $k$ is a proportionality constant.
	* *Not all periodic motion is harmonic. However, for small enough $A$, the motion is approximately harmonic*

* Simple Harmonic Motion is the projection of uniform circular motion onto a diameter. We refer to the analogous circle as the reference circle.
* *The angular speed of a reference circle is the angular frequency of the simple harmonic motion*
  
  $$
  \begin{split}
  \omega &= \sqrt\frac k m \\
  a &= \omega^2 x
  \end{split}
  $$

* *The period and frequency in Simple Harmonic Motion are independent of Amplitude*

* The [[Kinematics|displacement]] can be calculated as a function of time
  $$
  x(t) = A \cos (\omega t + \phi)
  $$
  Where $\phi$ is the **phase angle**, that is the initial angle in the reference circle. It is the point in the cycle the motion was at time $0$. 
	* Taking the derivative of the above gives the velocity and acceleration
	  $$
	  \begin{split}
	  v(t) &= -\omega A \sin (\omega t + \phi) \\
	  a(t) &= -\omega^2 A\cos (\omega t + \phi)
	  \end{split}
	  $$

* The total [[Work and Energy|energy]] present in simple harmonic motion is given by
  $$
  E = \frac{1}{2}kA^2 = \frac{1}{2}kx^2 + \frac{1}{2}mv^2 + c
  $$
	* Observe that when the object is displaced by its Amplitude, the Potential Energy is at its maximum. The Kinetic Energy is $0$ since the restoring force pulls the object back to equilibrium and at the amplitude (the farthest it goes), the object is at rest.
	* Conversely, at the equilibrium point, the velocity is at a maximum and the displacement point from the equilibrium point is $0$. The Potential Energy is $0$. 

# Angular Simple Harmonic Motion
* **Angular Simple Harmonic Motion** involves restoring [[Rotational Motion|torques]] proportional to an angular displacement $\theta$ from the equilibrium position.
* We have an analogue for Hooke's Law where $\kappa$ is the **torsion constant**
  $$
  \tau = -\kappa \theta
  $$
* The angular frequency and frequency are obtained by using the rotational analogues to mass
  $$
  \begin{split}
  \omega &= \sqrt{\frac \kappa I}\\
  \end{split}
  $$
  The angular displacement is obtained similarly
  $$
  \theta = \Theta \cos (\omega t + \phi)
  $$

# Simple Pendulum Motion
* A **simple pendulum** is an idealized model consisting of a point mass suspended by a massless, unstretchable string.
* The path of the point mass is an arc with radius $L$, the length of the string
  
  The tangential component of the force on the mass is given by
  $$
  F_\theta = -mg\sin \theta 
  $$
  We can use a first order approximation $\sin\theta \approx \theta$ [^pendulum] 
  $$
  F_\theta = -mg\theta = \frac{-mg}{L} x
  $$
* The angular frequency is given by
  $$
  \omega = \sqrt{\frac g L}
  $$
  *The period of the pendulum is independent of the mass of the bob. It is only dependent on the length of the string*

* Suppose the pendulum is not a point mass. Let $O$ be the pivot point (i.e., the axis of rotation) The center of gravity is $d$ units away from $O$. The weight of the object causes a restoring torque
  $$
  \tau = -mg d\sin \theta
  $$
  The torque is clockwise when the displacement is counterclockwise.
	* Using a first order approximation of $\sin\theta$ we have
	  $$
	  \omega = \sqrt{\frac{mgd}{I}}
	  $$
	* The above lets us calculate the moment of inertia given the object's mass and its behavior when allowed to oscillate and the distance $d$ to an axis of rotation.


[^pendulum]: This only works for small $\theta$ 

# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] - Ch. 14