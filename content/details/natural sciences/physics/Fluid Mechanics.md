* A **fluid** is any substance that can flow and change the shape of the volume that it occupies.

* A fluid has a **density** $\rho$ defined as
  
  $$
  \rho = \frac{m}{V}
  $$
	* The **specific gravity** oof a material is the ratio of its density to the density of water at $4.0\degree C$  -- $1000 kg/m^3$. 

# Pressure
* In a given fluid, the **pressure** applied to a body  is defined as 
  $$
  p = \frac{d\vec{F}_\perp}{dA}
  $$
  Where $\vec{F}$ is perpendicular to the surface with area $A$. 
	* *Pressure is scalar*. We can think of it as a proportionality constant.
	* If the pressure is the same at all points of the surface then 
	  $$
	  p = \frac{F_\perp}{A}
	  $$
* **Atmospheric Pressure** is the pressure exerted by the atmosphere. . **Gauge Pressure** is the excess pressure above atmospheric pressure. **Absolute Pressure** is the total pressure.

* **Pascal's Law** states that the *pressure applied to an enclosed fluid is transmitted undiminished to every portion of the fluid* and the walls of the containing vessel.
  
  The principle can be stated as follows for a fluid column in uniform [[Gravity]] and with uniform density
  
  $$
  \Delta p = \rho g \cdot \Delta h
  $$
  Where 
  $\Delta p$ is the difference in pressure at two points within the fluid column due to the weight of the fluid.
  $\Delta h$ is the difference in elevation between the two measurement points.
	* *Pressure between two elevations is due to the weight of the fluid between elevations*
	* This holds because the fluid is at equilibrium. Two forces cancel each other out -- the forces due to pressure from the surface to a cross section in the fluid applied on each other. What remains in the system is the weight of the top of the fluid surface exerted on the bottom.
	* This is the principle used by traditional pressure gauges. They measure the height differential resulting from applying pressure on a fluid.

* **Archimedes' Principle** When an object is completely or partially immersed in a fluid, the fluid exerts an upward force on the object equal to the weight of the fluid displaced by the object.
  
  $$
  F_b = -mg = -\rho V g 
  $$
	* If the buoyant object is in equilibrium, the only components of force contributing to it are in the axis of weight. Since no net motion exists, the fluid must exert an equal buoyant force. The weight is calculated as the amount of fluid displaced.

* **Surface Tension** - a phenomenon where the surface of a liquid behaves like a membrane under tension. Thus, *liquids minimize surface area*. 
	* It is due to the liquid's [[Chemistry|molecules]] exerting attractive forces on each other.  Molecules in the surface are drawn inwards which creates internal pressure and forces the liquid surface to minimize surface area.

# Flow
* An **ideal fluid** is incompressible (constant density) and has no internal friction (no viscosity). 
* The path of an individual particle in moving fluid is the **flow line**. 
* In **steady flow**, the flow pattern does not change with time. 
	* **Laminar flow** is a form of steady flow where adjacent lamina (thin layers) of fluid slide smoothly past each other .
	* A **turbulent flow** is one where the flow pattern does change. *Turbulent flow typically involves abrupt changes in velocity*.

* The **Volumetric Flow Rate** is defined as
  $$
  Q = \frac{dV}{dt}
  $$
  It is the flow of fluid $V$ through a surface per unit time $t$.
	* For uniform flow and a planar cross section
	  $$
	  Q =v\cdot A
	  $$
	  Where $v$ is the flow velocity and $A$ is the cross-sectional area vector / surface area
	* The general equation uses a [[Integral Calculus|surface integral]]
	  
	  $$
	  Q= \iint_A v \cdot dA
	  $$
	  Here, the vector area $A$ is defined using the magnitude of the area through which the volume passes through $\text{A}$ and the normal vector
	  $$
	  A = \text{A} \hat{n}
	  $$ 

* The **continuity equation** is based on the observation that *the mass of a fluid is invariant in flow*. The rate of mass entering a system is equal to the rate of mass leaving the system.
	* For an incompressible fluid, the continuity equation assuming the flow velocity field $u$ is
	  $$
	  \nabla \cdot u = 0
	  $$
	  Alternatively, this can also be written as
	  $$
	  A_1 v_1 = A_2v_2
	  $$
	  Where $A_1,A_2$ are the cross-sectional area at two points and $v_1,v_2$ are the flow velocity at two points
	  
	  Or using volumetric flow rate
	  $$
	  Q_1 = Q_2
	  $$

* **Bernoulli's Equation** relates flow speed $v$, pressure $p$, and height $y$ for flow of an ideal fluid.
  
  $$
  p + \rho g y + \frac{1}{2}\rho v^2 = k
  $$
  
	* This derives the [[Work and Energy|Work-Energy Theorem]], Pascual's Law and the Continuity Equation. An increase in speed (implying Kinetic Energy) corresponds to a decrease in height (Potential Energy) and pressure (Internal Energy).
	* *Assumptions*: Bernoulli's Equation assumes a steady flow, with an incompressible fluid where viscosity is negligible.

# Viscosity
* **Viscosity** is the internal friction in a fluid. 
	* A lower viscosity means that a fluid flows much easier.
	* *A viscous fluid always tends to cling to a solid surface in contact with it.* There is always a thin boundary layer of fluid near the surface, in which the fluid is nearly at rest with respect to the surface.
	* A greater viscosity means that the fluid tends to flow in a laminar manner.

# Turbulence
* **Turbulence** is irregular chaotic flow arising from the fluid flowing at a high speed.
# Links
* [[Kinds of Forces]]
* [[University Physics with Modern Physics 15th Edition By Freedman]]