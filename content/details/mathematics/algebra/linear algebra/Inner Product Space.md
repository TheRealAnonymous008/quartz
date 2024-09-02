* Inner product spaces add structure to [[Vector Space]] by introducing a notion of "distance".

# Basic Properties of Inner Products
* Let $V$ be a vector space over $F$. An **inner product** on $V$ is a function that assigns to every ordered pair $x,y\in V$ a scalar denoted $\braket{x,y}$ such that $\forall x, y, z\in V$ and $\forall c\in F$ the following hold
	* $\braket{x+z,y} = \braket{x,y} + \braket{z,y}$
	* $\braket{cx,y}=c\braket{x,y}$ 
	* $\overline{\braket{x,y}} =\braket{y,x}$. The LHS denotes **[[Complex Numbers and Quaternions|complex]] conjugation**
	* $\braket{x,x}>0$ if $x\ne 0$. 

* The following is immediately true for $a_1,\dots, a_n\in F$ and $x_1,\dots, x_n,y\in V$. 
  $$
  \bigg\langle{\sum_{i=1}^n a_i x_i, y}\bigg\rangle = \sum_{i=1}^n a_i \braket{x_i, y}
  $$
* A vector space with an inner product is called an **inner product space**. 


* (*Friedberg 6.1*) Let $V$ be an inner product space. Then for $x,y,z\in V$ and $c\in F$
	* $\braket{x,y+z}=\braket{x,y} + \braket{x,z}$. 
	* $\braket{x,cy}=\overline{c}\braket{x,y}$
	* $\braket{x,x}=0 \iff x=0$
	* $\braket{x,y}=\braket{x,z}$ $\forall x\in V$ implies that $y=z$. 

* The following is immediately true for $a_1,\dots, a_n\in F$ and $x,y_1,\dots, y_n\in V$. 
  $$
  \bigg\langle{x, \sum_{i=1}^n a_i y_i}\bigg\rangle = \sum_{i=1}^n \overline{a_i} \braket{x_i, y}
  $$
  That is, *inner products are conjugate linear in the second component*.

* Let $V$ be an inner product space. The **norm** of $x$ is defined as
  $$
  ||x|| = \sqrt{\braket{x,x}}
  $$
* (*Friedberg 6.2*) Let $V$ be an inner product space. Then $\forall x,y\in V, c\in F$ we have
	* $||cx|| = |c|\cdot ||x||$ 
	* $||x||=0 \iff x= 0$. Otherwise,  $||x||\ge 0$
	* **Cauchy Schwarz Inequality** 
	  $$
	  |\braket{x,y}| \le ||x|| \cdot ||y|| 
	  $$
	* **Triangle Inequality**
	  $$
	  ||x+y|| \le ||x|| + ||y||| 
	  $$

* The **distance** between $x$ and $y$, denoted $d(x,y)$ is defined as
  $$
  d(x,y) = ||x-y||
  $$
* (*Friedberg e6.1.23*) The following are true $\forall x, y, z \in V$
	* $d(x,y)\ge 0$ 
	* $d(x,y)=d(y,x)$
	* $d(x,y) \le d(x,z) + d(z,y)$
	* $d(x,x)=0$
	* $d(x,y\ne 0$  if $x\ne y$. 

* (*Friedberg e6.1.11*) The **Parallelogram Law** $\forall x, y\in V$
  $$
  ||x+y||^2 + ||x-y||^2 = 2||x||^2 + 2||y||^2
  $$

* (*Friedberg e6.1.20*) The **Polar Identitties**. $\forall x, y\in V$ where $V$ is over $F$
	* If $F=\mathbb{R}$ then 
	  $$
	  \braket{x,y}=\frac{1}{4} ||x+y||^2 - \frac{1}{4}||x-y||^2
	  $$
	* If $F=\mathbb{C}$ then
	  $$
	  \braket{x,y} = \frac{1}{4}\sum_{k=1}^4 i^k ||x+i^ky||^2 
	  $$ 
# Dot Product

* The **standard inner product** (also called the **dot product**) is defined such that 
  $$
   x\cdot y = \braket{x,y} = \sum_{i=1}^n a_i\overline{b_is}
  $$
* The Cauchy Schwarz Inequality for dot products:
  $$
  \left|\sum_{i=1}^n a_i\overline{b}_i \right| \le \left[\sum_{i=1}^n |a_i|^2\right]^{1/2} \left[\sum_{i=1}^n |b_i|^2\right]^{1/2} 
  $$

* The Triangle Inequality for dot products:
  $$
  \left[\sum_{i=1}^n |a_i + b_i|^2\right]^{1/2} \le \left[\sum_{i=1}^n |a_i|^2\right]^{1/2} + \left[\sum_{i=1}^n |b_i|^2\right]^{1/2} 
  $$

* (*Friedberg Lem.6.12.1*) Let $A\in M_{m\times n}(F)$, $x\in F^n$ and $y\in F^m$ then
  $$
  \braket{Ax,y}_m =\braket{x,A^\ast y}_n
  $$

# Topics
* [[Orthogonality and Orthonormality]]
* [[Matrix Conjugate and Adjoint]]
* [[Normal Matrix]]
* [[Self-Adjoint Matrix]]
* [[Unitary and Orthogonal Operators]]

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]