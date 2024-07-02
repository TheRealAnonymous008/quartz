* **Continuum Mechanics** studies the deformation and transmission of [[Kinds of Forces|forces]] through a continuous material.

# Stress and Strain
* **Stress** pertains to a force that causes a deformation on an object.
* **Strain** pertains to the deformation that results from strain.
* **Hooke's Law** states a relationship between the stress $\sigma$ and the strain $\varepsilon$ is given by
  $$
  \delta = \frac{\text{Stress}}{\text{Strain}} = \frac{\sigma}{\varepsilon}
  $$
  Where $\delta$ is the **elastic modulus**.
	* The elastic modulus depends on the material the object is made of.

* In general, the **stress** $\sigma$ experienced across a surface $S$ can have any direction relative to $S$

## Uniaxial Stress
* Let $\vec{F}_\perp$ be a force applied  perpendicular to the cross sectional area. When tension is acting on the object, then the **tensile stress** calculated as
  $$
  \sigma = \frac{\vec{F}_\perp}{A}
  $$
  When compression is acting on the object, then the **compressive stress** can be calculated instead. It is the same calculation above except $\vec{F}_\perp$ changes sign.
	* *This assumes that stress is evenly distributed over the entire cross section*
	* If the object has length $L$ with cross sectional area $D$ and has no defects, **Saint-Venant's principle** states that the stress can be assumed uniformly distributed over the cross sectional area over any cross section that is more than a few times $D$ from both ends.
* The **tensile / compressive strain** is defined by taking the change in length into account
  $$
  \varepsilon = \frac{\Delta l}{l_0}
  $$
* **Young's Modulus** is given as the elasticity modulus for tensile and compressive forces
  $$
  Y = \frac{\vec{F}_\perp \ \cdot l_0}{A \cdot \Delta l}
  $$
## Bulk Stress
* **Bulk Stress** acts on an object experiencing equal compression or tension in all directions and always directed perpendicularly to the surface independent of the surface's orientation. 
  
  If all the forces involved are compression forces, then the bulk stress is simply the [[Fluid Mechanics|pressure]] $p$.  
  
* The **Bulk Strain** is defined by
  $$
  \sigma = \frac{\Delta V}{V_0}
  $$
* The **Bulk Modulus** for compression / pressure  is defined as 
  $$
  B = - \frac{\Delta p}{\Delta V / V_0}
  $$
	* We include the negative sign to reflect the fact that increases in pressure mean a decrease in volume.
	* For small pressure changes in a solid or liquid, $B$ is constant. 
	* *The Bulk Modulus of a gas depends on the initial pressure* 
* The **compressibility** is defined as the reciprocal of the Bulk Modulus
  $$
  k = \frac{1}{B}
  $$

## Shear Stress
* **Shear stress** occurs when a uniformly thick layer is attached to two stiff bodies that are pulled in opposite directions in parallel directions. It is defined as 
  $$
  \sigma = \frac{\vec{F}_\parallel}{A}
  $$
	* Any plane perpendicular to the layer will have a net internal force and stress of $0$. 
	* Shear stress only applies to solid objects which have a definite shape.

* The **shear strain** is defined as the ratio of the displacement $x$ to the distance between the two surfaces $h$.
  
  $$
  \varepsilon = \frac{x}{h}
  $$

* The **Shear Modulus** is defined as
  $$
  S = \frac{\vec{F}_\parallel \cdot h}{A \cdot x}
  $$
![[Shear Stress.png]]
<figcaption> Shear Stress. Image taken from Freedman </figcaption>

## When Hooke's Law Doesn't Apply
* *Hooke's Law is not true in general. It assumes the material is sufficiently elastic*.
* There is a **proportional limit** such that beyond this point, Hooke's Law is no longer obeyed. 
* The **yield point** of an object is the point such that increasing the stress beyond this point causes an irreversible deformation on the object. 
	* Before the yield point is reached, the material is still **elastic** -- any deformation can be reversed by removing the stress
		* This is not necessarily true if the material has been stretched multiple times. In this case, the material experiences **elastic hysteresis** where, due to friction, the [[Work and Energy|work]] needed for the material to return the object to its original length is less than the work required to deform it. 
	* After the yield point is reached, the material is **plastic** -- any deformation due to stress cannot be reversed even if the stress is removed 
	* The **elastic limit** is the stress at the yield point.

* The **fracture point** is the point when a small stress causes a large strain to the point that the object breaks entirely.
	* The material's **breaking stress** is the amount of stress required to actually fracture the material.

* A material is **brittle** if it breaks soon after reaching its elastic limit. 
* A material is **ductile** if it can be given a large permanent stretch without breaking

# Links
* [[University Physics with Modern Physics 15th Edition By Freedman]] - Ch. 11
* [[Tensor Algebra]]