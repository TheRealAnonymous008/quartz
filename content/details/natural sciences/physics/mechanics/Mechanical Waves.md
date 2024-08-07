* A **mechanical wave** is a disturbance that travels through some material or substance called the **medium** of the wave.
	* A **transverse wave** is one where the medium is displaced perpendicular to the direction of travel of the wave.
	* A **longitudinal wave** is one where the medium is displaced parallel to the direction of travel of the wave.
	* *Waves can have both transverse and longitudinal components*

* All mechanical waves have the following in common:
	* The disturbance propagates with a definite [[Kinematics|speed]] through the medium called the **wave speed**
	* The medium does not travel through space. Instead, its particles undergo motions that displace it from the equilibrium position.
	* *Waves transport energy but not matter from one region to another.*

# Simple 1D Motion
* Simple mechanical waves can be created using [[Simple Harmonic Motion]] by applying a periodic force on one end of the medium. We call such waves **periodic waves**
	* Any periodic wave can be represented as a combination of [[Fourier Transform|sinusoidal waves]]
	* When a sinusoidal wave passes through a medium, *every particle in the medium undergoes simple harmonic motion with the same frequency.*
	* The shape is a repeated pattern. The **wavelength** is the distance from one point to the corresponding point in the next pattern instance. It is computed as
	  $$
	  v_P = \lambda f
	  $$
	  Here $v_P$ represents the **phase velocity**, also called the wave speed, the speed the disturbance propagates through the wave.

* The motion of a wave can be described using the following function. $x$ represents the distance from the start of the medium and $t$ represents time
  
  $$
  y(x,t) = A\cos \left[\omega \left(\frac{x}{t} + t\right)\right]
  $$
  This can also be described using the **angular wave number**
  $$
  \begin{split}
  k &= \frac{2\pi}{\lambda} \\ 
  y (x,t) &= A\cos \left[kx - \omega t\right]
  \end{split}
  $$
  Or the **wave number** 
  $$
  \begin{split}
  \tilde v &= \frac{1}{\lambda} \\
  y (x,t) &= A\cos \left[2\pi \tilde v\ x - \omega t\right]
  \end{split}
  $$
	* If we have a negative $\omega$, the wave travels in the negative direction.
	* The quantity $kx\pm \omega t$ is the **phase**. It determines what part of the sinusoidal cycle is occurring. 
		* *The phase of a wave does not change or vary with time*.
	* The wave speed is calculated as
	  $$
	  \frac{dx}{dt} = \frac \omega k 
	  $$
	* The kinematics of a sinusoidal wave are given by the following
	  $$
	  \begin{split}
	  \frac{\partial}{\partial t} y(x, t) &= \omega A \sin (kx -\omega t) \\
	  \frac{\partial^2}{\partial x^2} y(x,t) &= \frac{1}{v_P^2} \frac{\partial^2}{\partial t^2}y (x,t)
	  \end{split}
	  $$
	  The second formula is the wave equation in one dimension.  
* A wave's amplitude is independent of its wavelength or frequency.

* The wave speed is dependent on two factors -- a restoring force $F$ and an inertia resisting the return to equilibrium $\mu$
  
  $$
  v_P = \sqrt{\frac{F}{\mu}}
  $$
	* For a string under tension $T$ and linear density (density per unit length) $\mu$ is [^wave_speed]
	  $$
	  v_P = \sqrt{\frac T \mu}
	  $$

	* The average power of a sinusoidal wave is given by
	  $$
	  \overline P = \frac{1}{2}\sqrt{\mu F} \omega^2 A^2 
	  $$
	  The general equation for power is given by
	  $$
	  P(x,t) = F_y(x,t) v_y(x,t) = \sqrt{\mu F} \omega^2 A^2 \sin^2 (kx-\omega t)
	  $$
	  Where $F_y$ and $v_y$ are forces in the direction of the particle's motion.
	  
* A wave's **intensity** is the time average rate at which energy is transported by the wave per unit area. 
  
  It follows an inverse-square law where $r$ is the distance from the source
  $$
  \frac{I_1}{I_2} = \frac{r_2^2}{r_1^2}
  $$
  This assumes waves spread out equally in all directions. This result follows from the Conservation of Energy. The power outputted (energy per time) must be constant.
# Interacting Waves
* **Interference** happens when two or more waves pass through the same region at the same time.
* *When a wave travels and hits a boundary, the wave is reflected back which induces interference*.
	* If the medium exerted an upward force on a fixed boundary, a downward [[Newtonian Mechanics|reaction force]] is exerted on the medium and the pulse is sent "inverted"
	* On the other hand, if the medium exerted an upward force on a movable boundary, a pulse is sent from the boundary in an upward manner.

* If pulses overlap, the total displacement of the medium is the sum of the displacements at that point in the individual pulses.
  
  In general, the **principle of superposition** can be stated as follows
  
  $$
  y(x,t) = \sum_{i} y_i (x,t)
  $$
  Where $y$ is the wave function of the combined wave and the $y_i$'s are the individual wave functions.
  
  *This does not hold for all waves*, only waves whose mechanics allow for a motion that can be expressed as linearly (i.e. non-Hookean mediums do not exhibit this behavior) 

* A **standing wave** is a wave pattern which does not appear to be moving in either direction of the stream. This happens when two waves interfere with each other.
	* **Destructive Interference** - happens when two waves cancel each other because at that point they have equal and opposite displacement.
	* **Constructive Interference** - happens when two waves interfere in such a way that the resulting displacement is larger.

* In a standing wave, the **nodes** are the points where the medium never moves, and the **antinodes** are the points where the amplitude of string motion is greatest.
	* Antinodes are found halfway between two nodes.
	* Nodes are $\lambda/2$ apart.

* The wave function for a standing wave is given by
  
  $$
  y(x,t) = (A_\text{SW} \sin kx) \sin \omega t
  $$
  Where $A_\text{SW}$ is the amplitude of the standing wave. And we assume that the wave is fixed at $0$.

* *Standing waves do not transfer energy because at the points of destructive interference, the power from both sides cancel out*. The net effect is that no net energy is transferred.

* Consider a string of length $L$. By the nature of standing waves, the length $L$ of the string must be a multiple of half the wavelength 
  $$
  L = n\frac\lambda 2
  $$
  Since *the nodes of the wave must be half a wavelength apart. To support standing waves, $L$ needs to allow for this*

* The **fundamental frequency** of a waveform is defined as the one with the largest wavelength and the lowest frequency. That is
  $$
  f_1 = \frac{v}{2L} = \frac{1}{2L} \sqrt\frac T \mu
  $$
  The **Harmonic Series** is defined as
  $$
  f_n =n\frac{v}{2L} = \frac{n}{2L} \sqrt\frac T\mu
  $$

* A **normal mode** of an oscillating system is a motion where all particles move sinusoidally with the same frequency

# Generalizations
* The **Wave Equation** is a generalization to the relation between a wave's acceleration and its displacement. The $\nabla^2$ denotes the [[Differential Calculus|Laplacian]]. We have
  $$
  \frac{\partial^2 u }{\partial tt^2} = v^2 \nabla^2 u
  $$

[^wave_speed]: The intuition behind this is that, the total momentum increases with time due to the increasing mass being displaced. The mass displaced is equal to $\mu$ times the length displaced so far $v_Pt$. The momentum of each particle on the string is proportional to $F$. 
# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] - Ch. 15

* [[Periodic Motion]]
* [[Acoustics]]