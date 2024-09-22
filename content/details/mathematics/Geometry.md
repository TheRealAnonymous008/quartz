# Constructible Numbers
* A real number $\alpha$ is **constructible** if we can construct a line segment of length $|\alpha|$ in a finite number of steps from a given segment of unit length given a straightedge and compass.
* (*Fraleigh 32.1*) If $\alpha$ and $\beta$ are constructible real numbers, then so are $\alpha+\beta$, $\alpha-\beta$, $\alpha\beta$,  and if $\beta\ne 0$, $\alpha/\beta$. See the constructions below

![[Geometric Construction Sum and Difference.png]]
<figcaption> Geometric Construction of sum and difference. Image taken from Fraleigh  </figcaption>


![[Geometric Construction Product.png]]
<figcaption> Geometric Construction of product. Image taken from Fraleigh</figcaption>

![[Geometric Construction Quotient.png]]
<figcaption> Geometric Construction of quotient. Image taken from Fraleigh </figcaption>

* (*Fraleigh 32.5*) The set of all constructible real numbers forms a subfield $F$ of the [[Fundamental Constructs of Field Theory|field]] of real numbers.
* (*Fraleigh 32.6*) The field $F$ of constructible real numbers contains precisely of all real numbers that we can obtain from $\mathbb{Q}$ by taking square roots of positive numbers a finite number of times and applying a finite number of $+, -,\times, /$. 

![[Geometric Construction Square Root.png]]
<figcaption> Geometric construction of square root (specifically OQ has length that is the square root of a). Image taken from Fraleigh </figcaption>

* (*Fraleigh 32.8*) If $\gamma$ is constructible and $\gamma\notin \mathbb{Q}$, then there is a finite sequence of real numbers $\alpha_1,\dots, \alpha_n=\gamma$ such that $Q(\alpha_1,\dots,\alpha_i)$ is an [[Algebraic Extension|extension]] of $\mathbb{Q}(\alpha_1,\dots,\alpha_{i-1})$ of degree $2$. In particular for some integer $r\ge 0$ 
  $$
  [Q(\gamma) : Q] = 2^r
  $$

* (*Fraleigh 32.9*) **Doubling the Cube is impossible**. Given a side of a cube, it is not always possible to construct with a straightedge and compass, the side of a cube that has double the volume of the original cube.
	* *Proof*:  Doubling a cube requires the construction of the cube root, which is impossible unless $3$ is a power of $2$
* (*Fraleigh 32.10*) **Squaring the Circle is Impossible**. Given a circle, it is not always possible to construct with a straightedge and compass, a square having area equal to the area of the circle.
	* *Proof*: $\pi$ is [[Extension Field and Polynomials|transcendental]] over $\mathbb{Q}$ and also not representable using square roots. Therefore it is not constructible. 
* (*Fraleigh 32.11*) **Trisecting the angle is impossible**. There exists an angle that cannot be trisected with a straightedge and compass. 
	* *Proof*: The angle $\text{60}\degree$, if trisected, gives $20\degree$. But, it can be shown that $20\degree$ requires the use of cube roots to construct, which is impossible unless $3$ is a power of $2$. 


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]

* [2000 Years Unsolved: Why is doubling cubes and squaring circles impossible?](https://www.youtube.com/watch?v=O1sPvUr0YC0&t=113s)