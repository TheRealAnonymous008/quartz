* **Damping** arises when we have dissipative forces which cause an oscillation to die out.
* A simple case is when the damping force is proportional to the velocity of the oscillating object. That is, we have the force $F=-bv$, where $b$ is the damping constant

* This corresponds to the following [[Differential Equation]]
  $$
  -kx -b\frac{dx}{dt} = m \frac{d^2x}{dt^2}
  $$
  Which, for small damping, is solved by
  $$
  \begin{split}
  x &= Ae^{(-b/2m)t} \cos (\omega't+\phi) \\
  \omega' &= \sqrt{\frac{k}{m}-\frac{b^2}{4m^2}}
  \end{split}
  $$

* An oscillator achieves **critical damping** when the angular frequency is $0$. That is, when $b$ satisfies
  $$
  \frac{k}{m}-\frac{b^2}{4m^2} = 0
  $$
  or 
  $$
  b = 2\sqrt{km}
  $$
  Here the object no longer oscillates and returns to its equilibrium position when displaced and released

* An oscillator is **overdamped** when $b>2\sqrt{km}$.  Here there is no oscillation but the system returns to equilibrium more slowly than with critical damping

* An oscillator is **underdamped** when $b<2\sqrt{km}$. Here the system oscillates with steadily decreasing amplitude.

* *In damped oscillation, the damping force is non-conservative*. We have
  $$
  \frac{dE}{dt} = -bv^2
  $$
  This derives from the expression for energy in simple harmonic motion.
# Resonance
* A **driving force** is a force which is applied to a (damped) oscillator to maintain the amplitude. 
* The force can be applied with an angular frequency $\omega_D$. The motion is called a **driven oscillation**. We distinguish $\omega_D$ from the natural angular frequency $\omega'$ obtained from when we do not apply the driving force.
  
  The force is applied periodically say
  $$
  F(t) = F_\text{max} \cos \omega_D t
  $$
	* The amplitude of the driven oscillator is given by
	  $$
	  A = \frac{F_\text{max}}{\sqrt{(k-m\omega_d^2)^2 + b^2 \omega^2_d}}
	  $$
	* When $k-m\omega^2_d =0$, $A$ has a maximum near $\omega_d=\sqrt{\frac k m}$. The height of the curve is proportional to $\frac{1}{b}$. 
	* When $\omega_d = 0$, we have a constant displacement $A=F_\text{max}$

* **Resonance** - pertains to the peaking of the amplitude at driving frequencies close to the natural frequency of the system.

# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] - Ch. 14
* [[Simple Harmonic Motion]]