* A **complex Number** is a number that is of the form $$a+bi$$Where $a,b\in\mathbb{R}$ and $i=\sqrt{-1}$.

* **Euler's Formula** states that
  
  $$
  e^{i\theta}=\cos \theta + i\sin \theta
  $$
  Intuitively, this says that *an imaginary number captures the rotation on the unit circle.* This proof follows from expanding the [[Taylor Series|Taylor series]] of $e^x$ and extracting the terms corresponding to $\cos x$ and $\sin x$. 
  
  From this we derive **Euler's Identity** 
  
  $$
  e^{\pi i} - 1 = 0
  $$
* A **root of unity** is a complex number that when raised to a positive integer, results in $1$. 
  
  More formally, the $n$-th roots of unity are the complex solutions to the equation 
  
  $$
  x^n =1
  $$
	* The closed form of the $n$-th roots of unity can be obtained using Euler's Formula. We have that if $U_n$ is the set of $n$-th roots of unity, then 
	  
	  $$
	  U_n=\set{e^{2k\pi i/n} | k \in \set{1,2,\dots, n}}
	  $$
	  This follows immediately from Euler's identity . 
# Quaternion
* A **quaternion** $w+xi+yj+zk$ can be represented as the rotation corresponding to 
  $$
  \cos{\left(\frac{w}{2}\right)} + \sin{\left(\frac{w}{2}\right)}(x\hat{i}+y\hat{j}+z\hat{k})
  $$
* If we are given a Rotation [[Matrix|Matrix]] we can convert from quaternion to rotation matrix as follows
  $$
  \begin{bmatrix}
  1 - 2y^2 - 2z^2  & 2xy - wz &2xz + 2wy \\
  2xy + 2wz & 1-2x^2 -2z^2  & 2yz - 2wx \\
  2xz - 2wy & 2yz + 2wx & 1 - 2x^2 -2y^2
  \end{bmatrix}
  $$

# Links 
* [[Mathematics]]

* [Visualizing Quaternions (4d numbers) with stereographic projection](https://www.youtube.com/watch?v=d4EgbgTm0Bg)