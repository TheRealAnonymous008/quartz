* The **integral** of a function $f$ denotes the area under its curve. (If it is below zero, it is negative).  It is more formally defined as $$\int f(x)dx=\lim_{n\to \infty}\sum_{i=1}^{n}f(x_i)\Delta x$$Where the set of $x_i$ is a set of points spaced evenly. The intuition is that we take thin slices of the function.
* By the **Fundamental Theorem of Calculus**, the derivative and the integral are inverses of each other.
* **Iterated integrals** generalize integrals in that they take the volume under the surface of the function. The intuition is to take thin slices along each direction. 
* The **line integral** is an integral over a vector field $\vec{F}$ along a path $C$. It is denoted as $$\int_C\vec{F}(s)\cdot ds = \int_{t_0}^{t_1}F(r(t)) \cdot \frac{dr}{dt} dt$$The RHS of the above is a parameterization over $r(t)$, a function denoting the position at time $t$ if we perform a motion on $C$.
	* The **Fundamental Theorem of  Line Integrals** says that for a curve $C$ starting at point $P_0$ and ending at point $P_1$, we have that $$\int_C\nabla f\cdot ds=f(P_1)-f(P_0)$$That is, *gradient fields are path independent*, that is, the above integral holds for any $C$ that starts and ends at $P_0$ and $P_1$.
	  
	  This also implies the closed loop integral is defined as $$\oint_C\nabla f\cdot ds =0$$That is, *gradient fields are conservative*.
	  
	  This also implies that $\text{curl} \ F = \vec{0}$.
	* **Green's Theorem** says that if $C$ is a closed curve oriented counter clockwise enclosing region $R$ and a two-dimensional vector field $\vec{F}=\braket{L(x,y), M(x,y)}$ defined and differentiable in $R$. Then $$\oint_C(Ldx + Mdy) \cdot ds = \iint_R \left(\frac{\partial M}{\partial x}  - \frac{\partial M}{\partial y}\right) \ dA$$
	* **Green's Theorem** for flux says that if $C$ is a closed curve oriented counter clockwise enclosing region $R$ and a two-dimensional vector field $\vec{F}$ defined and differentiable in $R$. Then  $$\oint_C\vec{F}(s) \cdot \hat{n} \  ds = \iint_R (\nabla \cdot \vec{F}) \ dA$$
* The **surface integral** is an extension of the line integral, wherein we integrate over a surface $D$.  $dS$ denotes the surface area element. $$\iint_D\vec{F}(s)\cdot dS = \int_{t_0}^{t_1}F(r(t)) \cdot \frac{dr}{dt} dt$$
	* For a surface $S$, the **flux** measures the amount of the function $F$ that  passes through the surface $S$ (if we're dealing with lines, we simply use line integrals). It is defined as $$\iint_S\vec{F}(s)\cdot \hat{n} \ dS$$Where $\hat{n}$ is a unit normal vector pointing perpendicular to the surface $S$ 
	* The **Divergence Theorem** states that that for closed surface $S$ enclosing region $D$ and $\vec{F}$ a vector field defined and differentiable everywhere in $D$, then $${\subset\!\supset}\mathllap{\iint}_S(F\cdot\hat{n})dS=\iiint_D(\nabla\cdot F)\ dV$$Where $\hat{n}$ is oriented outwards from the surface $S$.
	  
	  Informally, *the sum of all sources of the field in a region gives the net flux in the region*
* **Stokes' Theorem** is a generalization of Green's Theorem for three dimensions. It states that for any line $C$ in space enclosing surface $S$, we have $$\oint_C\vec{F}\cdot ds=\iint_S(\nabla\times \vec{F}) \cdot \vec{n} \ dS$$Informally, *the line integral of a vector field over a loop is equal to the flux of its curl through the enclosed surface*.
  
  Note: the surface must be oriented following the right hand rule (thumb towards the curve, index towards the interior of the surface, middle finger points to normal). 
  
  The choice of surface doesn't matter as long as $C$ bounds it.
# Links
* [[Differential Calculus]]