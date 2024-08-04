* The **derivative**  $df/dx$ quantifies the instantaneous rate of change of a function. It is more formally defined as 
  $$
  \frac{df}{dx}=\lim_{h\to 0} \frac{f(x+h)-f(x)}{h}
  $$
  
* The **partial derivative** $\partial f / \partial x$ is a multivariable extension of the derivative that is calculated as the single variable derivative where all variables other than $x$ are held constant.
* The **Leibniz Integral Rule** for differentiation under the integral sign states that for an integral of the form
  
  $$
  \int_{a(x)}^{b(x)} f(x,t) \ dt 
  $$
  where $-\infty <a(x),b(x) <\infty$ has a derivative expressible as
  
  $$
  \frac{d}{dx}\left(\int_{a(x)}^{b(x)} f(x,t) \ dt\right) = f(x,b(x)) \cdot \frac{d}{dx} b(x) - f(x,a(x)) \cdot \frac{d}{dx}a(x) + \int_{a(x)}^{b(x)} \frac{\partial}{\partial x} f(x,t) \ dt
  $$
  
* The **Chain Rule** relates rates of changes between functions. It can be written as 
  $$
  \frac{df}{dt}=\frac{df}{dx}\frac{dx}{dt}
  $$
  For the multivariate case, it is simply 
  $$
  \frac{df}{dt}=\frac{df}{dx_1}\frac{dx_1}{dt} +\dots+\frac{df}{dx_n}\frac{dx_n}{dt}
  $$
  
* The **gradient** $\nabla f$ points to the direction of steepest ascent. It is perpendicular to the surface of the function.
	* Its components are the partial derivatives with respect to the coordinate system. That is
	  
	  $$
	  \begin{split}
	  \nabla f &= 
	  \begin{bmatrix} 
	  \partial f/\partial x_1 \\
	  \vdots \\
	  \partial f/ \partial x
	  \end{bmatrix}
	  \end{split}
	  $$
	* The dot product $\nabla f \cdot \hat{u}$ gives the **directional derivative**, the component of the gradient in the direction of $\hat{u}$
	* Let $\vec{F}=\nabla f$, then we say $\vec{F}$ is a **gradient field** and $f$ is the **potential function**.
* The **divergence** of a continuously differentiable vector field is calculated as 
  $$
  \text{div} \ F = \nabla \cdot F=\frac{\partial F}{\partial x_1} + \cdots +\frac{\partial F}{\partial x_n}
  $$
  
  It is a measure of how much nearby vectors are diverging.
* The **Laplacian** of a function is defined as 
  $$
  \Delta f = \nabla^2f=(\nabla \cdot \nabla) f = \frac{\partial^2 f}{\partial x_1^2}+\cdots+\frac{\partial^2f}{\partial x_n^2}
  $$
  
* The **curl** of $F=F_x i +F_y j +F_z k$ is defined as 
  $$
  \text{curl} \ F = \nabla\times F= \left|\begin{matrix}i & j & k \\
  \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial y} \\ 
  F_x & F_y & F_z
  \end{matrix}\right|
  $$
  It measures the vorticity of the vectors, that is the tendency for nearby vectors to move in a circular direction.
* The divergence and curl are related as follows 
  $$
  \nabla \cdot (\nabla\times F)=0
  $$
  That is, the divergence of the curl is $0$.
* **Lagrange Multipliers** work on the principle that given a function $f$ to be minimized subject to constraint $g$, they must satisfy  
  $$
  \nabla f=\lambda\nabla g
  $$
  That is, their normal vectors at the critical point must be parallel. $\lambda$ is the Lagrange Multiplier.
	* An alternative way to say this is to create the **Lagrangian**. That is, by creating a new function with which we minimize. This function is of the form 
	  $$
	  \mathcal{L}(x,\lambda)=f(x)+\lambda g(x)
	  $$
	  The derivative of which with respect to $x$ and $\lambda$ are minimized assuming we formulate that $g(x)=0$.
* The **Jacobian Matrix** of a function $f:\mathbb{R}^n \to \mathbb{R}^m$ is whose first order partial derivatives are defined, is defined as an $m\times n$ matrix $J$ where 
  $$
  J_{ij}=\frac{\partial f_i}{\partial x_j}
  $$
  Or as a matrix 
  $$
  J=\frac{\partial(f_1,\dots,f_m)}{\partial(x_1,\dots,x_n)} = \begin{bmatrix} 
  \nabla^Tf_1\\
  \vdots \\
  \nabla^Tf_m
  \end{bmatrix} = \begin{bmatrix}
  \frac{\partial f_1}{\partial x_1} & \cdots & \frac{\partial f_1}{\partial x_n} \\
  \vdots & \ddots & \vdots \\
  \frac{\partial f_m}{\partial x_1} & \cdots & \frac{\partial f_m}{\partial x_n}
  \end{bmatrix}
  $$
  
  Its determinant called the **Jacobian** denotes the relative change in volume near a point $p$. If it is positive it preserves orientation. Otherwise, it reverses orientation  
* The **Hessian Matrix** of a function $f:\mathbb{R^n}\to\mathbb{R}$ whose second order partial derivatives exist, is the square matrix $H$ where 
  $$
  H_{ij}=\frac{\partial ^2f}{\partial x_i\partial x_j}
  $$
  Its determinant is called the **Hessian**. 
  
  It is related to the Jacobian as followed: 
  $$
  H(f)=J(\nabla f)^T
  $$

# Theorems
* Let $a:\mathbb{R}\to\mathbb{R}^n$ and $b:\mathbb{R}\to \mathbb{R}^n$ be differentiable vector valued functions.
  
  The derivative of the dot product is given by
  $$
  \frac{d}{dx} (a\cdot b) = \frac{da}{dx} \cdot b + a\cdot \frac{db}{dx}
  $$
	* *Proof*: Use the definition of the dot product and apply the product rule

* Let $a:\mathbb{R}\to\mathbb{R}^3$ and $b:\mathbb{R}\to \mathbb{R}^3$ be differentiable vector valued functions.  
  
  The derivative of their cross product is given by
  
  $$
  \frac{d}{dx}(a\times b) = \frac{da}{dx} \times b + a \times \frac{db}{dx}
  $$
  
	* *Proof*: Use the definition of the cross product and apply the product rule

* Let $z: \mathbb{R}\to \mathbb{R}^n$ be a differentiable valued function such that each of its components $z_1\dots, z_n$ are differentiable real functions.
  
  Let $y:\mathbb{R}\to\mathbb{R}$ be a differentiable real-valued function. 
  
  Then
  
  $$
  \frac{d}{d x} (y z) = \frac{dy}{dx} z + y \frac{dz}{dx} 
  $$
  
# Links
* [[Integral Calculus]]
* [[Linear Algebra]]